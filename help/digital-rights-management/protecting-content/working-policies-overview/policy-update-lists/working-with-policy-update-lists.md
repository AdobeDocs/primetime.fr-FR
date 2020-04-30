---
seo-title: Utilisation des Listes de mise à jour des stratégies DRM
title: Utilisation des Listes de mise à jour des stratégies DRM
uuid: 41f89671-81c6-4d3d-ac31-9c2a1980517a
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# listes de mise à jour des stratégies DRM {#drm-policy-update-lists}

Si vous mettez à jour les règles d’utilisation dans une stratégie DRM après avoir compressé un contenu, le serveur de licences doit disposer de la dernière version pour pouvoir émettre des licences utilisant une stratégie DRM mise à jour. Pour y parvenir, une liste de mise à jour de la stratégie DRM permet de mettre à jour la stratégie DRM.

Une liste de mise à jour de stratégie DRM est représentée par un fichier qui inclut une liste de stratégies DRM mises à jour ou révoquées. Chaque fois que vous mettez à jour une stratégie DRM, vous devez générer une nouvelle Liste de mise à jour de la stratégie DRM et transmettre périodiquement la liste à tous les serveurs de licences.

## Utilisation des Listes de mise à jour des stratégies DRM {#working-with-drm-policy-update-lists}

Pour les serveurs de licences qui n’ont pas accès à une base de données pour stocker des informations sur les stratégies DRM, vous pouvez utiliser une liste de mise à jour de stratégie DRM pour avertir le serveur de licences de toute stratégie DRM mise à jour. Les Listes de mise à jour de la stratégie DRM peuvent inclure des versions mises à jour des stratégies DRM ou une liste d&#39;ID de stratégie DRM qui ont été révoqués. Si une liste de mise à jour de stratégie est incluse dans `HandlerConfiguration`, le SDK applique cette liste lorsqu’il délivre une licence.

Vous pouvez également révoquer toute stratégie DRM si les propriétaires ou les distributeurs de contenu veulent arrêter d’émettre des licences en vertu d’une stratégie DRM particulière. Une liste de mise à jour de stratégie DRM peut être utilisée pour appliquer la révocation de stratégie DRM dans le SDK. Vous pouvez également appliquer des listes de mise à jour de stratégie DRM pour fournir une liste de stratégies DRM mises à jour au SDK.

>[!NOTE]
>
>Chaque fois que vous révoquez une stratégie DRM, les licences déjà délivrées ne sont pas automatiquement révoquées. Il empêche seulement que des licences supplémentaires soient délivrées en vertu de cette politique de gestion des droits numériques.

## Mettre à jour les Listes de mise à jour des stratégies{#update-policy-update-lists}

L&#39;utilisation de listes de mise à jour de stratégie DRM implique l&#39;utilisation d&#39;un `PolicyUpdateListFactory` objet. Si vous souhaitez créer une liste de mise à jour de stratégie DRM, vous devez charger une liste de mise à jour de stratégie DRM existante, puis vérifier si une stratégie DRM a été mise à jour ou révoquée à l&#39;aide de l&#39;API Java.

Pour utiliser les Listes de mise à jour des stratégies DRM :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR inclus lors de la configuration de l’environnement de développement dans un projet.
1. Créez une `ServerCredentialFactory` instance pour charger les informations d’identification nécessaires à la signature.
1. Créez une `PolicyUpdateListFactory` instance à l’aide de la `ServerCredential` instance que vous avez créée.
1. Indiquez l’identifiant de stratégie DRM que vous souhaitez révoquer.
1. Créez un `PolicyRevocationEntry` objet en utilisant l&#39;ID de stratégie DRM `String` que vous venez de créer, puis ajoutez-le à la liste de mise à jour de la stratégie DRM en le transmettant `PolicyUpdateListFactory.addRevocationEntry()`.
1. Générez la nouvelle liste de mise à jour de la stratégie DRM en appelant `PolicyUpdateListFactory.generatePolicyUpdateList()`.

   De même, vous pouvez mettre à jour les stratégies DRM vers la liste en utilisant `PolicyUpdateEntry`.
1. Si une liste de mise à jour de stratégie DRM existe déjà, vous pouvez la sérialiser pour le chargement en appelant `PolicyUpdateList.getBytes()`.

   Pour charger la liste, appelez `PolicyUpdateListFactory.loadPolicyUpdateList()` et transmettez-la dans la liste sérialisée.
1. Vérifiez que la signature est valide et que la liste a été signée par le certificat du serveur de licences approprié en appelant `PolicyUpdateList.verifySignature()`.
1. Transférez l’identifiant de stratégie DRM `String` dans `PolicyUpdateList.isRevoked()` pour vérifier qu’une entrée a été révoquée.

   Vous pouvez également transmettre la liste à `HandlerConfiguration` l’endroit où elle est appliquée chaque fois que des licences sont délivrées.
Si vous souhaitez ajouter d&#39;autres entrées à une `PolicyUpdateList`stratégie existante, vous devez charger une liste de mise à jour de stratégie DRM existante. Par conséquent, vous devez créer une nouvelle `PolicyUpdateListFactory` instance DRM. Appelez `PolicyUpdateListFactory.addEntries` pour ajouter toutes les entrées de l&#39;ancienne liste à la nouvelle liste. Appelez `PolicyUpdateListFactory.addRevocationEntry` ou `addUpdatedEntry` pour ajouter toute nouvelle révocation ou entrée de mise à jour à DRM PolicyUpdateList.

Pour obtenir un exemple de code qui montre comment créer une liste de mise à jour de stratégie DRM, voir `com.adobe.flashaccess.samples.policyupdatelist``.CreatePolicyUpdateList` dans le répertoire Outils *de ligne de commande de mise en oeuvre de* référence [!DNL samples] .
