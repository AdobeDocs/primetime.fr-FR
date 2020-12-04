---
seo-title: Révocation des informations d’identification de l’ordinateur
title: Révocation des informations d’identification de l’ordinateur
uuid: 16119ff9-8147-4fe0-9744-a705d94a9400
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# Révocation des informations d’identification de l’ordinateur{#revoking-machine-credentials}

Adobe conserve une liste de révocation des certificats d’identification de l’ordinateur dont on sait qu’elle est compromise. Cette liste CRL est automatiquement appliquée par le SDK. S’il existe d’autres ordinateurs sur lesquels vous ne souhaitez pas que votre serveur de licences délivre des licences, vous pouvez créer une liste de révocation de l’ordinateur et ajouter le nom de l’émetteur et le numéro de série des jetons de l’ordinateur que vous souhaitez exclure (utilisez `MachineToken.getMachineTokenId()` pour récupérer le nom de l’émetteur et le numéro de série du certificat de l’ordinateur).

Le fait de révoquer les informations d&#39;identification de l&#39;ordinateur implique l&#39;utilisation d&#39;un objet `RevocationListFactory`. Pour créer une liste de révocation, chargez une liste de révocation existante et vérifiez si un jeton d’ordinateur a été révoqué à l’aide de l’API Java, procédez comme suit :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans [Configuration de l&#39;environnement de développement](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) dans votre projet.
1. Créez une instance `ServerCredentialFactory` pour charger les informations d’identification nécessaires à la signature. Les informations d’identification du serveur de licences sont utilisées pour signer la liste de révocation.
1. Créez une instance `RevocationListFactory`.
1. Indiquez l’émetteur et le numéro de série du jeton d’ordinateur à révoquer à l’aide d’un objet `IssuerAndSerialNumber`. Toutes les demandes d&#39;accès à l&#39;Adobe contiennent un jeton d&#39;ordinateur.
1. Créez un objet `RevocationList` à l&#39;aide de l&#39;objet `IssuerAndSerialNumber` que vous venez de créer et ajoutez-le à la liste de révocation en le transmettant dans `RevocationListFactory.addRevocationEntry()`. Générez la nouvelle liste de révocation en appelant `RevocationListFactory.generateRevocationList()`.
1. Pour enregistrer la liste de révocation, vous pouvez la sérialiser en appelant `RevocationList.getBytes()`. Pour charger la liste, appelez `RevocationListFactory.loadRevocationList()` et transmettez la liste sérialisée.
1. Vérifiez que la signature est valide et que la liste a été signée par le serveur de licences approprié en appelant `RevocationList.verifySignature()`.
1. Pour vérifier si une entrée a été révoquée, transmettez l&#39;objet `IssuerAndSerialNumber` dans `RevocationList.isRevoked()`. La liste de révocation peut également être transmise à `HandlerConfiguration` pour que le SDK applique la liste de révocation pour toutes les demandes d’authentification et de licence.

Pour ajouter des entrées supplémentaires à un `RevocationList` existant, chargez une liste de révocation existante. Créez une nouvelle instance `RevocationListFactory` et veillez à incrémenter le numéro CRL. Appelez `RevocationListFactioryEntries.addRevocationEntries` pour ajouter toutes les entrées de l&#39;ancienne liste à la nouvelle liste. Appelez `RevocationListFactory.addRevocationEntry` pour ajouter de nouvelles entrées de révocation à RevocationList.

Pour obtenir un exemple de code montrant comment créer une liste de révocation, charger une liste de révocation existante et vérifier si un jeton d&#39;ordinateur a été révoqué, voir `com.adobe.flashaccess.samples.revocation.CreateRevocationList` dans le répertoire &quot;samples&quot; des outils de ligne de commande de mise en oeuvre de référence.
