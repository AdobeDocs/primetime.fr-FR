---
description: Adobe Offline Packager prend comme entrée du contenu mp4 non chiffré.
seo-description: Adobe Offline Packager prend comme entrée du contenu mp4 non chiffré.
seo-title: Assemblage de votre contenu avec Adobe Offline Packager
title: Assemblage de votre contenu avec Adobe Offline Packager
uuid: d0676147-c20f-49ea-93a6-9c8dbbbba992
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Assemblage de votre contenu avec Adobe Offline Packager{#package-your-content-with-adobe-offline-packager}

Adobe Offline Packager prend comme entrée du contenu mp4 non chiffré.

**Appel d’Adobe Offline Packager**

Un appel standard d’adobe offline packager ressemble à l’appel ci-dessous :

    java -jar OfflinePackager.jar -conf_path Content_PR_WV.xml -in_path &quot;Jaigo.mp4&quot;
    -out_path &quot;Jaigo_DASH&quot;
    -key_file_path &quot;Jaigo_DASH/_info/key.B64.random&quot;
    -widevine_key_id c595f214d84dc7ecc7dc f31a8ebf1b7ddda5
    -widevine_provider intertrust
    -playready_LA_
    URLhttp://pr.test.expressplay.com/playready/RightsManager.asmx
    -playready_keyid c595f214d84dc7ecf31a8ebf1b7ddda5-content_id c595f21121 4d84dc7ecf31a8ebf1b7ddda5
    

Dans ce cas particulier, le gestionnaire de package hors ligne ajoute les données d’initialisation de protection de contenu Widevine et de protection de contenu PlayReady au contenu DASH de sortie. La valeur de `-key_file_path` est pour une clé codée en base 64. La valeur de `-playready_LA_URL` est pour l’acquisition de la licence PlayReady.

L&#39;argument conf_path pointe vers un fichier de configuration qui contiendrait les éléments suivants :

    &lt;config>
    &lt;frag_dur>4&lt;/frag_dur>
    &lt;_dur>6&lt;/_dur>
    &lt;encrypt_audio>false&lt;/encrypt_audio>
    &lt;/config>

Parce que certains périphériques Android — principalement Amazon Fire TV — ne prennent pas en charge le déchiffrement audio, le chiffrement audio est facultatif.
