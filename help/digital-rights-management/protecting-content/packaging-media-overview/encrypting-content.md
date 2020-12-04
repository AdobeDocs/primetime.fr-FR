---
seo-title: Chiffrement de contenu
title: Chiffrement de contenu
uuid: 03f33473-bcd4-4e06-a823-e944897cb28e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---


# Chiffrement de contenu {#encrypting-content}

Vous cryptez le contenu vidéo avec l’objet `MediaEncrypter`. Vous pouvez chiffrer des fichiers multimédias contenant uniquement des pistes audio. Vous pouvez également appliquer uniquement un chiffrement partiel ; par exemple, pour améliorer les performances lorsque vous chiffrez du contenu H.264 pour des périphériques bas de gamme.

Pour chiffrer des fichiers multimédia à l’aide de l’API Java :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans *Configuration de l&#39;environnement de développement* dans votre projet.
1. Créez une instance `ServerCredential` pour charger les informations d’identification nécessaires à la signature.
1. Créez une instance `MediaEncrypter`. Utilisez un `MediaEncryperFactory` si vous ne savez pas quel type de fichier vous avez.

1. Spécifiez les options de chiffrement en utilisant un objet `DRMParameters`.
1. Définissez les options de signature à l’aide d’un objet `SignatureParameters` et transmettez l’instance `ServerCredential` à sa méthode `setServerCredentials`.

1. Définissez la clé et les informations de licence à l’aide d’un objet `V2KeyParameters`. Définissez les stratégies DRM à l&#39;aide de la méthode `setPolicies`. Définissez les informations dont le client a besoin pour contacter le serveur de licences en appelant les méthodes `setLicenseServerUrl` et `setLicenseServerTransportCertificate`. Définissez les options de chiffrement CEK à l’aide de la méthode `setKeyProtectionOptions` et de ses propriétés personnalisées à l’aide de la méthode `setCustomProperties`. Enfin, selon le type de chiffrement utilisé, définissez l’objet `DRMKeyParameters` sur le type approprié ( `VideoDRMParameters`, `AudioDRMParameters`) et définissez les options de chiffrement.

1. Chiffrez le contenu en transmettant les fichiers d’entrée et de sortie et les options de chiffrement à la méthode `MediaEncrypter.encryptContent`.

Pour obtenir un exemple de code qui indique comment chiffrer du contenu, voir `com.adobe.flashaccess.samples.mediapackager.EncryptContent` dans le répertoire Reference Implementation Command Line Tools [!DNL samples/].
