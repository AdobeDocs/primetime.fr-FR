---
title: Utilisation des listes de mise à jour de stratégie DRM
description: Utilisation des listes de mise à jour de stratégie DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Listes de mise à jour des stratégies DRM {#drm-policy-update-lists}

Si vous mettez à jour les règles d’utilisation d’une stratégie DRM après avoir inclus un contenu, le serveur de licences doit disposer de la dernière version avant de pouvoir émettre des licences qui utilisent une stratégie DRM mise à jour. Pour ce faire, vous pouvez vous aider d’une liste de mise à jour des politiques DRM.

Une liste de mise à jour de stratégie DRM est représentée par un fichier qui inclut une liste de stratégies DRM mises à jour ou révoquées. Chaque fois que vous mettez à jour une stratégie DRM, vous devez générer une nouvelle liste de mise à jour de stratégie DRM et envoyer régulièrement la liste à tous les serveurs de licences.

## Utilisation des listes de mise à jour de stratégie DRM {#working-with-drm-policy-update-lists}

Pour les serveurs de licences qui n’ont pas accès à une base de données pour stocker des informations sur les stratégies DRM, vous pouvez utiliser une liste de mise à jour de stratégie DRM afin d’informer le serveur de licences de toute stratégie DRM mise à jour. Les listes de mise à jour de la stratégie DRM peuvent inclure des versions mises à jour des stratégies DRM ou une liste des ID de stratégie DRM qui ont été révoqués. Si une liste de mise à jour de stratégie est incluse dans `HandlerConfiguration`, le SDK applique cette liste lorsqu’il émet une licence.

Vous pouvez également révoquer toute stratégie DRM si les propriétaires ou les distributeurs de contenu veulent arrêter d’émettre des licences en vertu d’une stratégie DRM spécifique. Une liste de mise à jour de stratégie DRM peut être utilisée pour appliquer la révocation de la stratégie DRM dans le SDK. Vous pouvez également appliquer des listes de mise à jour de stratégie DRM pour fournir une liste des stratégies DRM mises à jour au SDK.

>[!NOTE]
>
>Chaque fois que vous révoquez une stratégie DRM, les licences déjà émises ne sont pas automatiquement révoquées. Il empêche uniquement l’émission de licences supplémentaires en vertu de cette politique DRM.

## Mettre à jour les listes de mise à jour des stratégies{#update-policy-update-lists}

L’utilisation de listes de mise à jour de stratégie DRM implique l’utilisation d’une `PolicyUpdateListFactory` . Si vous souhaitez créer une liste de mise à jour de stratégie DRM, vous devez charger une liste de mise à jour de stratégie DRM existante, puis vérifier si une stratégie DRM a été mise à jour ou révoquée à l’aide de l’API Java.

Pour utiliser les listes de mise à jour de stratégie DRM :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR inclus lors de la configuration de l’environnement de développement dans un projet .
1. Créez un `ServerCredentialFactory` pour charger les informations d’identification nécessaires à la signature.
1. Créez un `PolicyUpdateListFactory` en utilisant la fonction `ServerCredential` que vous avez créé.
1. Indiquez l’identifiant de stratégie DRM que vous souhaitez révoquer.
1. Créez un `PolicyRevocationEntry` en utilisant l’identifiant de stratégie DRM `String` que vous venez de créer, puis ajoutez-le à la liste de mise à jour de stratégie DRM en la transmettant `PolicyUpdateListFactory.addRevocationEntry()`.
1. Générez la nouvelle liste de mise à jour de stratégie DRM en appelant `PolicyUpdateListFactory.generatePolicyUpdateList()`.

   De même, vous pouvez mettre à jour les stratégies DRM dans la liste à l’aide de la fonction `PolicyUpdateEntry`.
1. Si une liste de mise à jour de stratégie DRM existe déjà, vous pouvez la sérialiser pour son chargement en appelant `PolicyUpdateList.getBytes()`.

   Pour charger la liste, appelez `PolicyUpdateListFactory.loadPolicyUpdateList()` et transmettez-le dans la liste sérialisée.
1. Vérifiez que la signature est valide et que la liste a été signée par le certificat du serveur de licences approprié en appelant `PolicyUpdateList.verifySignature()`.
1. Transmettre l’identifiant de stratégie DRM `String` into `PolicyUpdateList.isRevoked()` pour vérifier qu’une entrée a été révoquée.

   Vous pouvez également transmettre la liste à `HandlerConfiguration` où il est ensuite appliqué chaque fois que des licences sont émises.
Si vous souhaitez ajouter d’autres entrées à une `PolicyUpdateList`, vous devez charger une liste de mise à jour de stratégie DRM existante. Par conséquent, vous devez créer un DRM. `PolicyUpdateListFactory` instance. Appeler `PolicyUpdateListFactory.addEntries` pour ajouter à la nouvelle liste toutes les entrées de l’ancienne liste. Appeler `PolicyUpdateListFactory.addRevocationEntry` ou `addUpdatedEntry` pour ajouter de nouvelles entrées de révocation ou de mise à jour à DRM PolicyUpdateList.

Pour obtenir un exemple de code qui montre comment créer une liste de mise à jour de stratégie DRM, voir `com.adobe.flashaccess.samples.policyupdatelist` `.CreatePolicyUpdateList` dans le *Outils de ligne de commande de mise en oeuvre de référence* [!DNL samples] répertoire .
