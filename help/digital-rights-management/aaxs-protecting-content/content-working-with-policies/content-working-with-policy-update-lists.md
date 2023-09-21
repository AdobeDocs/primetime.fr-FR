---
title: Utilisation des listes de mise à jour de stratégie
description: Utilisation des listes de mise à jour de stratégie
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Utilisation des listes de mise à jour de stratégie{#working-with-policy-update-lists}

Pour les serveurs de licences qui n’ont pas accès à une base de données pour stocker des informations sur les stratégies, vous pouvez utiliser une liste de mise à jour de stratégie afin d’informer le serveur de licences des stratégies mises à jour. Les listes de mise à jour de stratégie peuvent contenir des versions mises à jour de stratégies ou une liste d’identifiants de stratégie révoqués. Si une liste de mise à jour de stratégie est fournie dans `HandlerConfiguration`, le SDK applique cette liste lors de l’émission d’une licence.

Les stratégies peuvent également être révoquées si les propriétaires ou les distributeurs de contenu veulent arrêter l’octroi des licences en vertu d’une stratégie spécifique. Une liste de mise à jour de stratégie peut être utilisée pour appliquer la révocation de la stratégie dans le SDK. Vous pouvez également utiliser des listes de mise à jour de stratégie pour fournir une liste des stratégies mises à jour au SDK. Notez que la révocation d’une stratégie ne révoque pas les licences qui ont déjà été émises. Il empêche uniquement l’octroi de licences supplémentaires en vertu de cette politique.

L’utilisation de listes de mise à jour de stratégie implique l’utilisation d’une `PolicyUpdateListFactory` . Pour créer une liste de mise à jour de stratégie, chargez une liste de mise à jour de stratégie existante et vérifiez si une stratégie a été mise à jour ou révoquée à l’aide de l’API Java, procédez comme suit :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans Configuration de l’environnement de développement dans votre projet.
1. Créez un `ServerCredentialFactory` pour charger les informations d’identification nécessaires à la signature.
1. Créez un `PolicyUpdateListFactory` à l’aide de la fonction `ServerCredential` vous avez créé.
1. Indiquez l’ID de stratégie à révoquer.
1. Créez un `PolicyRevocationEntry` à l’aide de l’identifiant de stratégie `String` vous venez de créer et de l’ajouter à la liste de mise à jour des stratégies en la transmettant `PolicyUpdateListFactory.addRevocationEntry()`. Générez la nouvelle liste de mise à jour des stratégies en appelant `PolicyUpdateListFactory.generatePolicyUpdateList()`. De même, les stratégies mises à jour peuvent être ajoutées à la liste à l’aide de `PolicyUpdateEntry`.
1. Si une liste de mise à jour de stratégie existe déjà, vous pouvez la sérialiser pour son chargement en appelant `PolicyUpdateList.getBytes()`. Pour charger la liste, appelez `PolicyUpdateListFactory.loadPolicyUpdateList()` et transmettez la liste sérialisée.
1. Vérifiez que la signature est valide et que la liste a été signée par le certificat du serveur de licences approprié en appelant `PolicyUpdateList.verifySignature()`.
1. Pour vérifier si une entrée a été révoquée, transmettez l’identifiant de stratégie. `String` into `PolicyUpdateList.isRevoked()`. Vous pouvez également transmettre la liste. `HandlerConfiguration` et elle sera appliquée lorsque des licences seront émises.

Pour ajouter des entrées supplémentaires à une `PolicyUpdateList`, chargez une liste de mise à jour de stratégie existante. Créer `PolicyUpdateListFactory` instance. Appelez P `olicyUpdateListFactory.addEntries` pour ajouter à la nouvelle liste toutes les entrées de l’ancienne liste. Appeler `PolicyUpdateListFactory.addRevocationEntry` ou `addUpdatedEntry` pour ajouter de nouvelles entrées de révocation ou de mise à jour à PolicyUpdateList.

Pour obtenir un exemple de code montrant comment créer une liste de mise à jour de stratégie, chargez une liste de mise à jour de stratégie existante et vérifiez si une stratégie a été révoquée, voir `com.adobe.flashaccess.samples.policyupdatelist` `.CreatePolicyUpdateList` dans le répertoire &quot;Exemples&quot; des outils de ligne de commande de mise en oeuvre de référence.
