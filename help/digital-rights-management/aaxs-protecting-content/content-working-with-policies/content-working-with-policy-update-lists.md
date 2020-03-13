---
seo-title: 'Utilisation du de mise à jour des stratégies '
title: 'Utilisation du de mise à jour des stratégies '
uuid: 583abb31-5c80-43f2-bc3d-a2300f61c4ea
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Utilisation du de mise à jour des stratégies{#working-with-policy-update-lists}

Pour les serveurs de licences qui n’ont pas accès à une base de données pour stocker des informations sur les stratégies, vous pouvez utiliser un de mise à jour de stratégie pour avertir le serveur de licences des stratégies mises à jour. Le de mise à jour de stratégie peut contenir des versions mises à jour de stratégies ou un d’ID de stratégie qui ont été révoqués. Si un de mise à jour de stratégie est fourni dans `HandlerConfiguration`, le SDK applique ce  lors de l’émission d’une licence.

Les stratégies peuvent également être révoquées si les propriétaires ou les distributeurs de contenu souhaitent cesser d’émettre des licences en vertu d’une stratégie particulière. Un de mise à jour de stratégie peut être utilisé pour appliquer la révocation de stratégie dans le SDK. Le de mise à jour de stratégie peut également être utilisé pour fournir un de stratégies mises à jour au SDK. Notez que la révocation d’une stratégie ne révoque pas les licences qui ont déjà été émises. Elle empêche uniquement l’émission de licences supplémentaires en vertu de cette politique.

L’utilisation d’un de mise à jour de stratégie implique l’utilisation d’un `PolicyUpdateListFactory` objet. Pour créer un  de mise à jour de stratégie, chargez un de mise à jour de stratégie existant et vérifiez si une stratégie a été mise à jour ou révoquée à l’aide de l’API Java, procédez comme suit :

1. Configurez votre  de développement   et incluez tous les fichiers JAR mentionnés dans Configuration du de développement  dans votre projet.
1. Créez une `ServerCredentialFactory` instance pour charger les informations d’identification nécessaires à la signature.
1. Créez une `PolicyUpdateListFactory` instance à l’aide de la `ServerCredential` instance que vous avez créée.
1. Spécifiez l’ID de stratégie à révoquer.
1. Créez un `PolicyRevocationEntry` objet à l’aide de l’ID de stratégie `String` que vous venez de créer, puis ajoutez-le au de mise à jour de stratégie en le transmettant `PolicyUpdateListFactory.addRevocationEntry()`. Générez le nouveau de mise à jour de stratégie en appelant `PolicyUpdateListFactory.generatePolicyUpdateList()`. De même, des stratégies mises à jour peuvent être ajoutées au  du à l’aide de `PolicyUpdateEntry`.
1. Si un de mise à jour de stratégie existe déjà, vous pouvez le sérialiser en vue de son chargement en appelant `PolicyUpdateList.getBytes()`. Pour charger le , appelez `PolicyUpdateListFactory.loadPolicyUpdateList()` et transmettez le sérialisé.
1. Vérifiez que la signature est valide et que le  a été signé par le certificat du serveur de licences approprié en appelant `PolicyUpdateList.verifySignature()`.
1. Pour vérifier si une entrée a été révoquée, transmettez l’ID de stratégie `String` dans `PolicyUpdateList.isRevoked()`. Vous pouvez également transmettre le  `HandlerConfiguration` et l’appliquer lors de l’émission des licences.

Pour ajouter des entrées supplémentaires à un existant `PolicyUpdateList`, chargez un  de mise à jour de stratégie existant. Créez une `PolicyUpdateListFactory` instance. Appelez P `olicyUpdateListFactory.addEntries` pour ajouter toutes les entrées de l&#39;ancien au nouvel . Appelez `PolicyUpdateListFactory.addRevocationEntry` ou `addUpdatedEntry` ajoutez toute nouvelle révocation ou entrée de mise à jour à PolicyUpdateList.

Pour obtenir un exemple de code qui montre comment créer un de mise à jour de stratégie, charger un de mise à jour de stratégie existant et vérifier si une stratégie a été révoquée, reportez-vous `com.adobe.flashaccess.samples.policyupdatelist` au répertoire &quot;samples&quot; des outils de ligne de commande de mise en oeuvre de référence `.CreatePolicyUpdateList` dans la section.
