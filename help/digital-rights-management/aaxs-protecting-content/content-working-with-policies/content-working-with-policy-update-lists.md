---
seo-title: Utilisation des Listes de mise à jour des stratégies
title: Utilisation des Listes de mise à jour des stratégies
uuid: 583abb31-5c80-43f2-bc3d-a2300f61c4ea
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Utilisation des Listes de mise à jour des stratégies{#working-with-policy-update-lists}

Pour les serveurs de licences qui n’ont pas accès à une base de données pour stocker des informations sur les stratégies, vous pouvez utiliser une liste de mise à jour de stratégie pour avertir le serveur de licences de stratégies mises à jour. Les Listes de mise à jour de stratégie peuvent contenir des versions mises à jour de stratégies ou une liste d’ID de stratégie qui ont été révoqués. Si une liste de mise à jour de stratégie est fournie dans `HandlerConfiguration`, le SDK applique cette liste lors de l’émission d’une licence.

Les stratégies peuvent également être révoquées si les propriétaires ou les distributeurs de contenu souhaitent cesser d’émettre des licences en vertu d’une stratégie particulière. Une liste de mise à jour de stratégie peut être utilisée pour appliquer la révocation de stratégie dans le SDK. Des listes de mise à jour de stratégie peuvent également être utilisées pour fournir une liste de stratégies mises à jour au SDK. Notez que la révocation d’une stratégie ne révoque pas les licences déjà délivrées. Elle empêche seulement les licences supplémentaires d&#39;être délivrées en vertu de cette politique.

L’utilisation de listes de mise à jour de stratégie implique l’utilisation d’un `PolicyUpdateListFactory` objet. Pour créer une liste de mise à jour de stratégie, chargez une liste de mise à jour de stratégie existante et vérifiez si une stratégie a été mise à jour ou révoquée à l’aide de l’API Java, procédez comme suit :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans Configuration de l’environnement de développement dans votre projet.
1. Créez une `ServerCredentialFactory` instance pour charger les informations d’identification nécessaires à la signature.
1. Créez une `PolicyUpdateListFactory` instance à l’aide de la `ServerCredential` instance que vous avez créée.
1. Spécifiez l’ID de stratégie à révoquer.
1. Créez un `PolicyRevocationEntry` objet à l’aide de l’ID de stratégie `String` que vous venez de créer et ajoutez-le à la liste de mise à jour de stratégie en le transmettant `PolicyUpdateListFactory.addRevocationEntry()`. Générez la nouvelle liste de mise à jour de stratégie en appelant `PolicyUpdateListFactory.generatePolicyUpdateList()`. De même, des stratégies mises à jour peuvent être ajoutées à la liste à l’aide de `PolicyUpdateEntry`.
1. Si une liste de mise à jour de stratégie existe déjà, vous pouvez la sérialiser en vue de son chargement en appelant `PolicyUpdateList.getBytes()`. Pour charger la liste, appelez `PolicyUpdateListFactory.loadPolicyUpdateList()` et transmettez la liste sérialisée.
1. Vérifiez que la signature est valide et que la liste a été signée par le certificat du serveur de licences approprié en appelant `PolicyUpdateList.verifySignature()`.
1. Pour vérifier si une entrée a été révoquée, transmettez l’identifiant de stratégie `String` à `PolicyUpdateList.isRevoked()`. Sinon, la liste peut être transmise `HandlerConfiguration` et elle sera appliquée lorsque des licences seront délivrées.

Pour ajouter d’autres entrées à un `PolicyUpdateList`fichier existant, chargez une liste de mise à jour de stratégie existante. Créez une nouvelle `PolicyUpdateListFactory` instance. Appelez P `olicyUpdateListFactory.addEntries` pour ajouter toutes les entrées de l&#39;ancienne liste à la nouvelle liste. Appelez `PolicyUpdateListFactory.addRevocationEntry` ou `addUpdatedEntry` pour ajouter toute nouvelle révocation ou entrée de mise à jour à PolicyUpdateList.

Pour obtenir un exemple de code montrant comment créer une liste de mise à jour de stratégie, charger une liste de mise à jour de stratégie existante et vérifier si une stratégie a été révoquée, voir `com.adobe.flashaccess.samples.policyupdatelist``.CreatePolicyUpdateList` dans le répertoire &quot;samples&quot; des outils de ligne de commande de mise en oeuvre de référence.
