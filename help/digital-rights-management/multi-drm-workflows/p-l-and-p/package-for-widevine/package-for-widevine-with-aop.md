---
description: Adobe Offline Packager prend comme entrée du contenu mp4 non chiffré.
title: Regroupez votre contenu avec Adobe Offline Packager
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Regroupez votre contenu avec Adobe Offline Packager{#package-your-content-with-adobe-offline-packager}

Adobe Offline Packager prend comme entrée du contenu mp4 non chiffré.

**Appel de Adobe Offline Packager**

Un appel type d’adobe offline packager ressemble à l’appel ci-dessous :

    java -jar OfflinePackager.jar -conf_path Content_PR_WV.xml -in_path &quot;Jaigo.mp4&quot;
    -out_path &quot;Jaigo_DASH&quot;
    -key_file_path &quot;Jaigo_DASH/_info/key.B64.random&quot;
    -widevine_key_id c595f214d84dc7ecf31a8ebf1b7ddda5
    -widevine_provider intertrust
    -playready_LA_URL
    http://pr.test.expressplay.com/playready/RightsManager.asmx
    -playready_keyid c595f214d84dc7ecf31a8ebf1b7ddda5
    -content_id c595f214d84dc7ecf31a8ebf1b7ddda5

Dans ce cas particulier, le programme de package hors ligne ajoute les données d’initialisation de protection de contenu Windows et PlayReady au contenu DASH de sortie. La valeur de `-key_file_path` est pour une clé codée en base64. La valeur de `-playready_LA_URL` est destiné à l’acquisition de la licence PlayReady .

L’argument conf_path pointe vers un fichier de configuration qui contiendra les éléments suivants :

    &lt;config>
    &lt;frag_dur>4&lt;/frag_dur>
    &lt;target_dur>6&lt;/target_dur>
    &lt;encrypt_audio>false&lt;/encrypt_audio>
    &lt;/config>

Comme certains appareils Android — principalement Amazon Fire TV — ne prennent pas en charge le décryptage audio, le chiffrement audio est facultatif.
