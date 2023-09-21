---
title: Chiffrement du contenu
description: Chiffrement du contenu
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Chiffrement du contenu{#encrypting-content}

Le cryptage du contenu FLV et F4V implique l’utilisation d’un `MediaEncrypter` . Vous pouvez également compresser des fichiers FLV et F4V contenant uniquement des pistes audio. Lors du chiffrement du contenu H.264 pour les périphériques bas de gamme, il peut s’avérer pratique d’appliquer uniquement un chiffrement partiel afin d’améliorer les performances. Dans ce cas, un fichier F4V peut être partiellement chiffré à l’aide de la fonction `F4VDRMParameters.setVideoEncryptionLevel`.

Pour chiffrer un fichier FLV ou F4V à l’aide de l’API Java, procédez comme suit :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans Configuration de l’environnement de développement dans votre projet.
1. Créez un `ServerCredential` pour charger les informations d’identification nécessaires à la signature.
1. Créez un `MediaEncrypter` instance. Utilisez une `MediaEncryperFactory` si vous ne savez pas quel type de fichier vous disposez. Sinon, vous pouvez créer une `FLVEncrypter` ou `F4VEncrypter` directement.
1. Définissez les options de chiffrement à l’aide d’une `DRMParameters` .
1. Définissez les options de signature à l’aide d’une `SignatureParameters` et transmettez la variable `ServerCredential` à `setServerCredentials` .
1. Définissez la clé et les informations de licence à l’aide d’une `V2KeyParameters` . Définissez les stratégies à l’aide de la variable `setPolicies` . Définissez les informations dont le client a besoin pour contacter le serveur de licences en appelant le `setLicenseServerUrl` et `setLicenseServerTransportCertificate` méthodes. Définissez les options de chiffrement du CEK à l’aide de la fonction `setKeyProtectionOptions` et ses propriétés personnalisées à l’aide de la méthode `setCustomProperties` . Enfin, selon le type de chiffrement utilisé, jetez la variable `DRMKeyParameters` à l’un des objets `VideoDRMParameters`, `AudioDRMParameters`, `FLVDRMParameters`, ou `F4VDRMParameters`et définissez les options de chiffrement.
1. Chiffrez le contenu en transmettant les fichiers d’entrée et de sortie et les options de chiffrement au `MediaEncrypter.encryptContent` .

Pour obtenir un exemple de code montrant comment chiffrer du contenu, voir `com.adobe.flashaccess.samples.mediapackager.EncryptContent` dans le répertoire &quot;Exemples&quot; des outils de ligne de commande de mise en oeuvre de référence.
