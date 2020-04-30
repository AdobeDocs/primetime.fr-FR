---
seo-title: Révocation des informations d’identification de l’ordinateur
title: Révocation des informations d’identification de l’ordinateur
uuid: 3647c843-5f1a-457e-949d-10a6278b1c29
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Révocation des informations d’identification de l’ordinateur {#revoking-machine-credentials}

Adobe conserve une liste de révocation des certificats d’identification de l’ordinateur qui sont connus pour être compromis. Cette liste CRL est automatiquement appliquée par le SDK. S’il existe d’autres ordinateurs sur lesquels vous ne souhaitez pas que votre serveur de licences délivre des licences, vous pouvez créer une liste de révocation de l’ordinateur et ajouter le nom et le numéro de série de l’émetteur des jetons de l’ordinateur que vous souhaitez exclure (à utiliser `MachineToken.getMachineTokenId()` pour récupérer le nom de l’émetteur et le numéro de série du certificat de l’ordinateur).

Le fait de rappeler les informations d’identification de l’ordinateur implique l’utilisation d’un `RevocationListFactory` objet. Pour créer une liste de révocation, chargez une liste de révocation existante et vérifiez si un jeton d’ordinateur a été révoqué à l’aide de l’API Java, procédez comme suit :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans [Configuration de l’environnement](../../protecting-content/setting-up-the-sdk/setup-dev-env.md) de développement dans votre projet.
1. Créez une `ServerCredentialFactory` instance pour charger les informations d’identification nécessaires à la signature. Les informations d’identification du serveur de licences sont utilisées pour signer la liste de révocation.
1. Créez une `RevocationListFactory` instance.
1. Indiquez l’émetteur et le numéro de série du jeton de l’ordinateur à révoquer à l’aide d’un `IssuerAndSerialNumber` objet. Toutes les demandes DRM Adobe Primetime contiennent un jeton d’ordinateur.
1. Créez un `RevocationList` objet à l’aide de l’ `IssuerAndSerialNumber` objet que vous venez de créer et ajoutez-le à la liste de révocation en le transmettant `RevocationListFactory.addRevocationEntry()`. Générez la nouvelle liste de révocation en appelant `RevocationListFactory.generateRevocationList()`.

1. Pour enregistrer la liste de révocation, vous pouvez la sérialiser en appelant `RevocationList.getBytes()`. Pour charger la liste, appelez `RevocationListFactory.loadRevocationList()` et transmettez la liste sérialisée.

1. Vérifiez que la signature est valide et que la liste a été signée par le serveur de licences approprié en appelant `RevocationList.verifySignature()`.
1. Pour vérifier si une entrée a été révoquée, transmettez l’ `IssuerAndSerialNumber` objet dans `RevocationList.isRevoked()`. La liste de révocation peut également être transmise pour que le SDK applique la liste de révocation `HandlerConfiguration` pour toutes les demandes d’authentification et de licence.

Pour ajouter d’autres entrées à une liste de révocation existante `RevocationList`, chargez-la. Créez une nouvelle `RevocationListFactory` instance et veillez à incrémenter le numéro de la liste CRL. Appelez `RevocationListFactioryEntries.addRevocationEntries` pour ajouter toutes les entrées de l&#39;ancienne liste à la nouvelle liste. Appelez `RevocationListFactory.addRevocationEntry` pour ajouter de nouvelles entrées de révocation à RevocationList.

Pour obtenir un exemple de code qui montre comment créer une liste de révocation, charger une liste de révocation existante et vérifier si un jeton d’ordinateur a été révoqué, voir `com.adobe.flashaccess.samples.revocation.CreateRevocationList` dans le [!DNL samples] répertoire Outils de ligne de commande de mise en oeuvre de référence.
