---
seo-title: Révocation des informations d’identification de l’ordinateur
title: Révocation des informations d’identification de l’ordinateur
uuid: 3647c843-5f1a-457e-949d-10a6278b1c29
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Révocation des informations d’identification de l’ordinateur {#revoking-machine-credentials}

Adobe conserve une liste de révocation des informations d’identification de l’ordinateur dont on sait qu’elles sont compromises. Cette liste CRL est automatiquement appliquée par le SDK. S’il existe d’autres ordinateurs sur lesquels vous ne souhaitez pas que votre serveur de licences délivre des licences, vous pouvez créer un de révocation de l’ordinateur et ajouter le nom et le numéro de série de l’émetteur des jetons de l’ordinateur que vous souhaitez exclure (à utiliser `MachineToken.getMachineTokenId()` pour récupérer le nom et le numéro de série de l’émetteur du certificat de l’ordinateur).

Le fait de rappeler les informations d’identification de l’ordinateur implique l’utilisation d’un `RevocationListFactory` objet. Pour créer un  de révocation, chargez un de révocation existant et vérifiez si un jeton d’ordinateur a été révoqué à l’aide de l’API Java, procédez comme suit :

1. Configurez votre  de développement   et incluez tous les fichiers JAR mentionnés dans [Configuration du](../../protecting-content/setting-up-the-sdk/setup-dev-env.md) de développement  dans votre projet.
1. Créez une `ServerCredentialFactory` instance pour charger les informations d’identification nécessaires à la signature. Les informations d’identification du serveur de licences sont utilisées pour signer le  de révocation.
1. Créez une `RevocationListFactory` instance.
1. Spécifiez l’émetteur et le numéro de série du jeton de l’ordinateur à révoquer à l’aide d’un `IssuerAndSerialNumber` objet. Toutes les demandes DRM Adobe Primetime contiennent un jeton d’ordinateur.
1. Créez un `RevocationList` objet à l’aide de l’ `IssuerAndSerialNumber` objet que vous venez de créer, puis ajoutez-le au de révocation en le transmettant `RevocationListFactory.addRevocationEntry()`. Générez le nouveau de révocation en appelant `RevocationListFactory.generateRevocationList()`.

1. Pour enregistrer le  de révocation, vous pouvez le sérialiser en appelant `RevocationList.getBytes()`. Pour charger le , appelez `RevocationListFactory.loadRevocationList()` et transmettez le sérialisé.

1. Vérifiez que la signature est valide et que le a été signé par le serveur de licences approprié en appelant `RevocationList.verifySignature()`.
1. Pour vérifier si une entrée a été révoquée, transmettez l’ `IssuerAndSerialNumber` objet dans `RevocationList.isRevoked()`. Le de révocation peut également être transmis `HandlerConfiguration` pour que le SDK applique le de révocation pour toutes les demandes d’authentification et de licence.

Pour ajouter des entrées supplémentaires à un existant `RevocationList`, chargez un  de révocation existant. Créez une nouvelle `RevocationListFactory` instance et veillez à incrémenter le nombre de listes CRL. Appelez `RevocationListFactioryEntries.addRevocationEntries` pour ajouter toutes les entrées de l&#39;ancien au nouvel . Appelez `RevocationListFactory.addRevocationEntry` pour ajouter de nouvelles entrées de révocation à RevocationList.

Pour obtenir un exemple de code qui montre comment créer un  de révocation, charger un de révocation existant et vérifier si un jeton d’ordinateur a été révoqué, reportez-vous `com.adobe.flashaccess.samples.revocation.CreateRevocationList` au répertoire des outils de ligne de commande d’implémentation de référence [!DNL samples] .
