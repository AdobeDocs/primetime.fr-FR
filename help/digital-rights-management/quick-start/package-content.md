---
seo-title: Assemblage de contenu chiffré
title: Assemblage de contenu chiffré
uuid: 1e271167-107d-41df-8a7c-3075cb3acc0c
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Assemblage de contenu chiffré{#package-encrypted-content}

1. Copiez le `<Primetime DRM DVD>\Reference Implementation\Command Line Tools\` répertoire dans votre système de fichiers local.
1. Dans votre `Command Line Tools\` dossier local, mettez à jour le `flashaccesstools.properties` fichier afin qu’il fonctionne avec votre serveur.

   Vous devez modifier au moins les propriétés suivantes :

   * `encrypt.keys.asymmetric.certfile=[license-server-certificate.cer]`: Chemin d’accès à votre certificat de serveur de licences (il se termine généralement par [!DNL .cer], [!DNL .der] ou [!DNL .pem]).

   * `encrypt.license.serverurl=[license-server-url]`: L’URL de votre serveur de licences, par exemple :    `https://<License Server Hostname>:8080/flashaccessserver/sampletenant`.

   * `encrypt.license.servercert=[transport-certificate.cer]`: Chemin d’accès à votre certificat de transport (il se termine généralement par [!DNL .cer], [!DNL .der]ou [!DNL .pem]).

   * `encrypt.sign.certfile=[packager-credentials.pfx]`: Chemin d’accès à votre certificat Packager (qui se termine par [!DNL .pfx]).

   * `encrypt.sign.certpass=[password]`: mot de passe de votre certificat Packager.
   >[!NOTE]
   >
   >Veillez à ne pas brouiller le mot de passe.

1. Créez une stratégie.

   Dans votre `Command Line Tools\` dossier local, exécutez la commande suivante :

   ```
   java -jar libs/AdobePolicyManager.jar new examplepolicy.pol -n examplepolicy -x
   ```

   Cette commande crée un fichier de stratégie nommé [!DNL examplepolicy.pol] qui utilise l’authentification anonyme du serveur de licences ( `-x` option).
1. Copiez le fichier vidéo MP4, FLV ou F4V que vous souhaitez chiffrer dans votre `Command Line Tools\` dossier local.
1. Assemblez votre contenu.

   Supposons que votre fichier vidéo source soit [!DNL sample.mp4]. Dans votre `Command Line Tools\` dossier local, exécutez la commande suivante :

   ```
   java -jar libs/AdobePackager.jar sample.mp4 sample_encrypted.mp4 -p examplepolicy.pol
   ```

   >[!NOTE]
   >
   >Si vous souhaitez compresser le contenu HLS, HDS ou DASH, vous devez utiliser un autre outil de création de package, tel qu’ [Adobe Primetime Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf).

1. Copiez les artefacts de fichier chiffrés (dans ce cas [!DNL sample_encrypted.mp4] et [!DNL sample_encrypted.mp4.metadata]) dans `<Your Content Server - Tomcat Install Dir>\webapps\ROOT`.

A ce stade, vous avez terminé la phase d&#39;emballage du processus.

>[!NOTE]
>
>Pour plus d’informations sur les outils de ligne de commande permettant d’empaqueter du contenu, de créer des stratégies, etc., voir Outils [en ligne de commande](../drm-reference-implementations/command-line-tools/command-line-tools-overview.md)Adobe Primetime DRM.
