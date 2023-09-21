---
title: Chiffrement du contenu
description: Chiffrement du contenu
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Chiffrement du contenu{#encrypting-content}

Vous chiffrez le contenu vidéo à l’aide de la fonction `MediaEncrypter` . Vous pouvez chiffrer les fichiers multimédias qui ne contiennent que des pistes audio. Vous pouvez également appliquer un chiffrement partiel uniquement ; par exemple, pour améliorer les performances lorsque vous chiffrez du contenu H.264 pour des appareils de niveau inférieur.

Pour chiffrer des fichiers multimédias à l’aide de l’API Java :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans *Configuration de l’environnement de développement* dans votre projet.
1. Créez un `ServerCredential` pour charger les informations d’identification nécessaires à la signature.
1. Créez un `MediaEncrypter` instance. Utilisez une `MediaEncryperFactory` si vous ne savez pas quel type de fichier vous disposez.

1. Définissez les options de chiffrement à l’aide d’une `DRMParameters` .
1. Définissez les options de signature à l’aide d’une `SignatureParameters` et transmettez la variable `ServerCredential` à `setServerCredentials` .

1. Définissez la clé et les informations de licence à l’aide d’une `V2KeyParameters` . Définissez les stratégies DRM à l’aide de la variable `setPolicies` . Définissez les informations dont le client a besoin pour contacter le serveur de licences en appelant le `setLicenseServerUrl` et `setLicenseServerTransportCertificate` méthodes. Définissez les options de chiffrement du CEK à l’aide de la fonction `setKeyProtectionOptions` et ses propriétés personnalisées à l’aide de la méthode `setCustomProperties` . Enfin, selon le type de chiffrement utilisé, jetez la variable `DRMKeyParameters` vers le type approprié ( `VideoDRMParameters`, `AudioDRMParameters`), puis définissez les options de chiffrement.

1. Chiffrez le contenu en transmettant les fichiers d’entrée et de sortie et les options de chiffrement au `MediaEncrypter.encryptContent` .

Pour obtenir un exemple de code qui indique comment chiffrer du contenu, voir `com.adobe.flashaccess.samples.mediapackager.EncryptContent` dans les outils de ligne de commande de mise en oeuvre de référence [!DNL samples/] répertoire .
