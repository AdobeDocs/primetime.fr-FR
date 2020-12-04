---
seo-title: Chiffrement de contenu
title: Chiffrement de contenu
uuid: ea71154e-557b-447e-bc14-208232f00be1
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---


# Chiffrement de contenu {#encrypting-content}

Le chiffrement du contenu FLV et F4V implique l’utilisation d’un objet `MediaEncrypter`. Vous pouvez également assembler des fichiers FLV et F4V contenant uniquement des pistes audio. Lorsque vous chiffrez du contenu H.264 pour des périphériques bas de gamme, il peut s’avérer pratique d’appliquer uniquement un chiffrement partiel afin d’améliorer les performances. Dans ce cas, un fichier F4V peut être partiellement chiffré à l’aide de la méthode `F4VDRMParameters.setVideoEncryptionLevel`.

Pour chiffrer un fichier FLV ou F4V à l’aide de l’API Java, procédez comme suit :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans Configuration de l’environnement de développement dans votre projet.
1. Créez une instance `ServerCredential` pour charger les informations d’identification nécessaires à la signature.
1. Créez une instance `MediaEncrypter`. Utilisez un `MediaEncryperFactory` si vous ne savez pas quel type de fichier vous avez. Sinon, vous pouvez créer directement un `FLVEncrypter` ou `F4VEncrypter`.
1. Spécifiez les options de chiffrement en utilisant un objet `DRMParameters`.
1. Définissez les options de signature à l’aide d’un objet `SignatureParameters` et transmettez l’instance `ServerCredential` à sa méthode `setServerCredentials`.
1. Définissez la clé et les informations de licence à l’aide d’un objet `V2KeyParameters`. Définissez les stratégies à l&#39;aide de la méthode `setPolicies`. Définissez les informations dont le client a besoin pour contacter le serveur de licences en appelant les méthodes `setLicenseServerUrl` et `setLicenseServerTransportCertificate`. Définissez les options de chiffrement CEK à l’aide de la méthode `setKeyProtectionOptions` et de ses propriétés personnalisées à l’aide de la méthode `setCustomProperties`. Enfin, selon le type de chiffrement utilisé, définissez l&#39;objet `DRMKeyParameters` sur l&#39;un des éléments suivants : `VideoDRMParameters`, `AudioDRMParameters`, `FLVDRMParameters` ou `F4VDRMParameters`, puis définissez les options de chiffrement.
1. Chiffrez le contenu en transmettant les fichiers d’entrée et de sortie et les options de chiffrement à la méthode `MediaEncrypter.encryptContent`.

Pour obtenir un exemple de code montrant comment chiffrer du contenu, voir `com.adobe.flashaccess.samples.mediapackager.EncryptContent` dans le répertoire &quot;samples&quot; des outils de ligne de commande de mise en oeuvre de référence.
