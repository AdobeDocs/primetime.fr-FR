---
title: Contenu chiffré du package
description: Contenu chiffré du package
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# Contenu chiffré du package {#package-encrypted-content}

1. Copiez le répertoire `<Primetime DRM DVD>\Reference Implementation\Command Line Tools\` dans votre système de fichiers local.
1. Dans votre dossier `Command Line Tools\` local, mettez à jour le fichier `flashaccesstools.properties` pour qu’il fonctionne avec votre serveur.

   Vous devez modifier au moins les propriétés suivantes :

   * `encrypt.keys.asymmetric.certfile=[license-server-certificate.cer]`: Chemin d’accès à votre certificat de serveur de licences (il se termine généralement par  [!DNL .cer] [!DNL .der] ou  [!DNL .pem]).

   * `encrypt.license.serverurl=[license-server-url]`: URL de votre serveur de licences, par exemple :     `https://<License Server Hostname>:8080/flashaccessserver/sampletenant`.

   * `encrypt.license.servercert=[transport-certificate.cer]`: Chemin d&#39;accès à votre certificat de transport (il se termine généralement par  [!DNL .cer],  [!DNL .der] ou  [!DNL .pem]).

   * `encrypt.sign.certfile=[packager-credentials.pfx]`: Chemin d’accès à votre certificat Packager (qui se termine par  [!DNL .pfx]).

   * `encrypt.sign.certpass=[password]`: Mot de passe de votre certificat Packager.
   >[!NOTE]
   >
   >Veillez à ne pas brouiller le mot de passe.

1. Créez une stratégie.

   Dans votre dossier local `Command Line Tools\`, exécutez la commande suivante :

   ```
   java -jar libs/AdobePolicyManager.jar new examplepolicy.pol -n examplepolicy -x
   ```

   Cette commande crée un fichier de stratégie nommé [!DNL examplepolicy.pol] qui utilise l&#39;authentification anonyme du serveur de licences (l&#39;option `-x`).
1. Copiez le fichier vidéo MP4, FLV ou F4V que vous souhaitez chiffrer dans votre dossier local `Command Line Tools\`.
1. Empaquetez votre contenu.

   Supposons que votre fichier vidéo source soit [!DNL sample.mp4]. Dans votre dossier local `Command Line Tools\`, exécutez la commande suivante :

   ```
   java -jar libs/AdobePackager.jar sample.mp4 sample_encrypted.mp4 -p examplepolicy.pol
   ```

   >[!NOTE]
   >
   >Si vous souhaitez compresser le contenu HLS, HDS ou DASH, vous devez utiliser un autre outil de création de package, tel que [Adobe Primetime Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf).

1. Copiez les artefacts de fichier chiffrés (dans ce cas [!DNL sample_encrypted.mp4] et [!DNL sample_encrypted.mp4.metadata]) dans `<Your Content Server - Tomcat Install Dir>\webapps\ROOT`.

À ce stade, vous avez terminé la phase d&#39;emballage du processus.

>[!NOTE]
>
>Pour plus d&#39;informations sur les outils de ligne de commande permettant d&#39;empaqueter du contenu, de créer des stratégies, etc., voir [Adobe Primetime DRM Command-line tools](../drm-reference-implementations/command-line-tools/command-line-tools-overview.md).
