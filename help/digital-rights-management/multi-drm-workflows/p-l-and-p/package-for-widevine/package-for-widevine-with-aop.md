---
description: Adobe Offline Packager prend comme entrée du contenu mp4 non chiffré.
title: Assemblage de votre contenu avec Adobe Offline Packager
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Mettez en package votre contenu avec Adobe Offline Packager{#package-your-content-with-adobe-offline-packager}

Adobe Offline Packager prend comme entrée du contenu mp4 non chiffré.

**Appel d&#39;Adobe Hors ligne Packager**

Un appel standard d’adobe offline packager ressemblerait à l’appel ci-dessous :

    java -jar OfflinePackager.jar -conf_path Content_PR_WV.xml -in_path &quot;Jaigo.mp4&quot;
    -out_path &quot;Jaigo_DASH&quot;
    -key_file_path &quot;Jaigo_DASH/_info/key.B64.random&quot;
    -widevine_key_id c595f214d84ecdc7dc f31a8ebf1b7ddda5
    -widevine_provider intertrust
    -playready_LA_
    URLhttp://pr.test.expressplay.com/playready/RightsManager.asmx
    -playready_keyid c595f214d84dc7ecf31a8ebf1b7ddda5-content_id c595f2114d84dc7ecf31a8ebf1b7ddda5

    
Dans ce cas particulier, le gestionnaire de package hors ligne ajoute les données d&#39;initialisation de protection de contenu Widevine et de protection de contenu PlayReady au contenu DASH de sortie. La valeur `-key_file_path` correspond à une clé codée en base 64. La valeur de `-playready_LA_URL` correspond à l’acquisition de la licence PlayReady.

L&#39;argument conf_path pointe vers un fichier de configuration qui contiendra les éléments suivants :

    &lt;config>
    &lt;frag_dur>4&lt;/frag_dur>
    &lt;target_dur>6&lt;/target_dur>
    &lt;encrypt_audio>false&lt;/encrypt_audio>
    &lt;/config>

Certains périphériques Android, principalement Amazon Fire TV, ne prenant pas en charge le déchiffrement audio, le chiffrement audio est facultatif.
