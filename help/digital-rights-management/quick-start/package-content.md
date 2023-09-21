---
title: Contenu chiffré du package
description: Contenu chiffré du package
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Contenu chiffré du package{#package-encrypted-content}

1. Copiez le `<Primetime DRM DVD>\Reference Implementation\Command Line Tools\` à votre système de fichiers local.
1. Dans votre `Command Line Tools\` , mettez à jour le dossier `flashaccesstools.properties` pour travailler avec votre serveur.

   Vous devez modifier au moins les propriétés suivantes :

   * `encrypt.keys.asymmetric.certfile=[license-server-certificate.cer]`: chemin d’accès à votre certificat de serveur de licences (il se termine généralement par [!DNL .cer], [!DNL .der] ou [!DNL .pem]).

   * `encrypt.license.serverurl=[license-server-url]`: l’URL de votre serveur de licences, par exemple :    `https://<License Server Hostname>:8080/flashaccessserver/sampletenant`.

   * `encrypt.license.servercert=[transport-certificate.cer]`: chemin d’accès à votre certificat de transport (il se termine généralement par [!DNL .cer], [!DNL .der], ou [!DNL .pem]).

   * `encrypt.sign.certfile=[packager-credentials.pfx]`: chemin d’accès à votre certificat Packager (qui se termine par [!DNL .pfx]).

   * `encrypt.sign.certpass=[password]`: mot de passe de votre certificat Packager.

   >[!NOTE]
   >
   >Veillez à ne pas brouiller le mot de passe.

1. Créez une stratégie.

   Dans votre `Command Line Tools\` , exécutez la commande suivante :

   ```
   java -jar libs/AdobePolicyManager.jar new examplepolicy.pol -n examplepolicy -x
   ```

   Cette commande crée un fichier de stratégie nommé [!DNL examplepolicy.pol] qui utilise l’authentification anonyme du serveur de licences (le `-x` ).
1. Copiez le fichier vidéo MP4, FLV ou F4V que vous souhaitez chiffrer dans votre fichier local. `Command Line Tools\` dossier.
1. Regroupez votre contenu.

   Supposons que votre fichier vidéo source soit [!DNL sample.mp4]. Dans votre `Command Line Tools\` , exécutez la commande suivante :

   ```
   java -jar libs/AdobePackager.jar sample.mp4 sample_encrypted.mp4 -p examplepolicy.pol
   ```

   >[!NOTE]
   >
   >Si vous souhaitez regrouper des contenus HLS, HDS ou DASH, vous devez utiliser un autre outil de création de packages, tel que [Adobe Primetime Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf).

1. Copiez les artefacts de fichier chiffrés (ici : [!DNL sample_encrypted.mp4] et [!DNL sample_encrypted.mp4.metadata]) à `<Your Content Server - Tomcat Install Dir>\webapps\ROOT`.

A ce stade, vous avez terminé la phase de conditionnement du processus.

>[!NOTE]
>
>Pour plus d’informations sur les outils de ligne de commande permettant de grouper le contenu, de créer des stratégies, etc., voir [Outils de ligne de commande Adobe Primetime DRM](../drm-reference-implementations/command-line-tools/command-line-tools-overview.md).
