---
seo-title: Utilisation des Listes de mise à jour des stratégies
title: Utilisation des Listes de mise à jour des stratégies
uuid: 583abb31-5c80-43f2-bc3d-a2300f61c4ea
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# Utilisation des Listes de mise à jour des stratégies{#working-with-policy-update-lists}

Pour les serveurs de licences qui n’ont pas accès à une base de données pour stocker des informations sur les stratégies, vous pouvez utiliser une liste de mise à jour de stratégie pour avertir le serveur de licences de stratégies mises à jour. Les Listes de mise à jour de stratégie peuvent contenir des versions mises à jour de stratégies ou une liste d’ID de stratégie qui ont été révoqués. Si une liste de mise à jour de stratégie est fournie dans `HandlerConfiguration`, le SDK applique cette liste lors de l’émission d’une licence.

Les stratégies peuvent également être révoquées si les propriétaires ou les distributeurs de contenu souhaitent cesser d’émettre des licences en vertu d’une stratégie particulière. Une liste de mise à jour de stratégie peut être utilisée pour appliquer la révocation de stratégie dans le SDK. Des listes de mise à jour de stratégie peuvent également être utilisées pour fournir une liste de stratégies mises à jour au SDK. Notez que la révocation d’une stratégie ne révoque pas les licences déjà délivrées. Elle empêche seulement les licences supplémentaires d&#39;être délivrées en vertu de cette politique.

L&#39;utilisation de listes de mise à jour de stratégie implique l&#39;utilisation d&#39;un objet `PolicyUpdateListFactory`. Pour créer une liste de mise à jour de stratégie, chargez une liste de mise à jour de stratégie existante et vérifiez si une stratégie a été mise à jour ou révoquée à l’aide de l’API Java, procédez comme suit :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans Configuration de l’environnement de développement dans votre projet.
1. Créez une instance `ServerCredentialFactory` pour charger les informations d’identification nécessaires à la signature.
1. Créez une instance `PolicyUpdateListFactory` à l&#39;aide de `ServerCredential` que vous avez créée.
1. Spécifiez l’ID de stratégie à révoquer.
1. Créez un objet `PolicyRevocationEntry` à l&#39;aide de l&#39;ID de stratégie `String` que vous venez de créer et ajoutez-le à la liste de mise à jour de stratégie en le transmettant dans `PolicyUpdateListFactory.addRevocationEntry()`. Générez la nouvelle liste de mise à jour de stratégie en appelant `PolicyUpdateListFactory.generatePolicyUpdateList()`. De même, des stratégies mises à jour peuvent être ajoutées à la liste à l&#39;aide de `PolicyUpdateEntry`.
1. Si une liste de mise à jour de stratégie existe déjà, vous pouvez la sérialiser pour le chargement en appelant `PolicyUpdateList.getBytes()`. Pour charger la liste, appelez `PolicyUpdateListFactory.loadPolicyUpdateList()` et transmettez la liste sérialisée.
1. Vérifiez que la signature est valide et que la liste a été signée par le certificat du serveur de licences approprié en appelant `PolicyUpdateList.verifySignature()`.
1. Pour vérifier si une entrée a été révoquée, transmettez l&#39;ID de stratégie `String` dans `PolicyUpdateList.isRevoked()`. Vous pouvez également transmettre la liste à `HandlerConfiguration` et l&#39;appliquer lors de l&#39;émission des licences.

Pour ajouter des entrées supplémentaires à une `PolicyUpdateList` existante, chargez une liste de mise à jour de stratégie existante. Créez une nouvelle instance `PolicyUpdateListFactory`. Appelez P `olicyUpdateListFactory.addEntries` pour ajouter toutes les entrées de l&#39;ancienne liste à la nouvelle liste. Appelez `PolicyUpdateListFactory.addRevocationEntry` ou `addUpdatedEntry` pour ajouter toute nouvelle révocation ou entrée de mise à jour à PolicyUpdateList.

Pour obtenir un exemple de code montrant comment créer une liste de mise à jour de stratégie, charger une liste de mise à jour de stratégie existante et vérifier si une stratégie a été révoquée, voir `com.adobe.flashaccess.samples.policyupdatelist` `.CreatePolicyUpdateList` dans le répertoire &quot;samples&quot; des outils de ligne de commande de mise en oeuvre de référence.
