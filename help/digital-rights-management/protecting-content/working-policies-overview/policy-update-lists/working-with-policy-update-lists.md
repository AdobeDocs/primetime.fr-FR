---
seo-title: 'Utilisation du de mise à jour de la stratégie DRM '
title: 'Utilisation du de mise à jour de la stratégie DRM '
uuid: 41f89671-81c6-4d3d-ac31-9c2a1980517a
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


#  de mise à jour de la stratégie DRM {#drm-policy-update-lists}

Si vous mettez à jour les règles d’utilisation dans une stratégie DRM après avoir compressé un contenu, le serveur de licences doit disposer de la dernière version avant de pouvoir émettre des licences utilisant une stratégie DRM mise à jour. Pour ce faire, vous pouvez utiliser un de mise à jour de stratégie DRM.

Un de mise à jour de stratégie DRM est représenté par un fichier qui inclut un de stratégies DRM mises à jour ou révoquées. Chaque fois que vous mettez à jour une stratégie DRM, vous devez générer un nouveau de mise à jour de stratégie DRM et pousser régulièrement le vers tous les serveurs de licences.

## Utilisation du de mise à jour de la stratégie DRM {#working-with-drm-policy-update-lists}

Pour les serveurs de licences qui n’ont pas accès à une base de données pour stocker des informations sur les stratégies DRM, vous pouvez utiliser un de mise à jour de stratégie DRM pour avertir le serveur de licences de toute stratégie DRM mise à jour. Le de mise à jour de la stratégie DRM peut inclure des versions mises à jour des stratégies DRM ou un d’ID de stratégie DRM qui ont été révoqués. Si un de mise à jour de stratégie est inclus dans `HandlerConfiguration`, le SDK applique ce  lorsqu’il délivre une licence.

Vous pouvez également révoquer toute stratégie DRM si les propriétaires ou les distributeurs de contenu souhaitent cesser d’émettre des licences en vertu d’une stratégie DRM particulière. Un de mise à jour de stratégie DRM peut être utilisé pour appliquer la révocation de stratégie DRM dans le SDK. Vous pouvez également appliquer le de mise à jour de stratégie DRM pour fournir un de stratégies DRM mises à jour au SDK.

>[!NOTE]
>
>Chaque fois que vous révoquez une stratégie DRM, les licences déjà émises ne sont pas automatiquement révoquées. Elle empêche uniquement l’émission de licences supplémentaires en vertu de cette politique de gestion des droits numériques.

## Mettre à jour les  de mise à jour des stratégies{#update-policy-update-lists}

L’utilisation du de mise à jour de stratégie DRM implique l’utilisation d’un `PolicyUpdateListFactory` objet. Si vous souhaitez créer un de mise à jour de stratégie DRM, vous devez charger un de mise à jour de stratégie DRM existant, puis vérifier si une stratégie DRM a été mise à jour ou révoquée à l’aide de l’API Java.

Pour travailler avec le de mise à jour des stratégies DRM :

1. Configurez votre  de développement  et incluez tous les fichiers JAR inclus lors de la configuration du de développement  dans un projet.
1. Créez une `ServerCredentialFactory` instance pour charger les informations d’identification nécessaires à la signature.
1. Créez une `PolicyUpdateListFactory` instance à l’aide de la `ServerCredential` instance que vous avez créée.
1. Spécifiez l’ID de stratégie DRM que vous souhaitez révoquer.
1. Créez un `PolicyRevocationEntry` objet à l’aide de l’ID de stratégie DRM `String` que vous venez de créer, puis ajoutez-le au de mise à jour de la stratégie DRM en le transmettant `PolicyUpdateListFactory.addRevocationEntry()`.
1. Générez le nouveau de mise à jour de stratégie DRM en appelant `PolicyUpdateListFactory.generatePolicyUpdateList()`.

   De même, vous pouvez mettre à jour les stratégies DRM vers le  à l’aide de `PolicyUpdateEntry`.
1. Si un de mise à jour de stratégie DRM existe déjà, vous pouvez le sérialiser en vue de son chargement en appelant `PolicyUpdateList.getBytes()`.

   Pour charger le , appelez `PolicyUpdateListFactory.loadPolicyUpdateList()` et transmettez-le dans le sérialisé.
1. Vérifiez que la signature est valide et que le a été signé par le certificat du serveur de licences approprié en appelant `PolicyUpdateList.verifySignature()`.
1. Transférez l’ID de stratégie DRM `String` dans `PolicyUpdateList.isRevoked()` pour vérifier qu’une entrée a été révoquée.

   Vous pouvez également transmettre le  à `HandlerConfiguration` l’endroit où il est appliqué chaque fois que des licences sont délivrées.
Si vous souhaitez ajouter d’autres entrées à un existant `PolicyUpdateList`, vous devez charger un  de mise à jour de stratégie DRM existant. Par conséquent, vous devez créer une nouvelle `PolicyUpdateListFactory` instance DRM. Appelez `PolicyUpdateListFactory.addEntries` pour ajouter toutes les entrées de l&#39;ancien au nouvel . Appelez `PolicyUpdateListFactory.addRevocationEntry` ou `addUpdatedEntry` ajoutez toute nouvelle révocation ou entrée de mise à jour à la liste de mise à jour de stratégie DRM.

Pour obtenir un exemple de code qui montre comment créer un de mise à jour de stratégie DRM, reportez-vous `com.adobe.flashaccess.samples.policyupdatelist` au répertoire `.CreatePolicyUpdateList` Référence Implementation Command Line Tools *Tools (Outils* de ligne de commande d’implémentation de [!DNL samples] référence).
