---
description: Nous utilisons à la fois le gestionnaire de package Bento4 et le gestionnaire de package hors ligne Adobe pour créer du contenu DASH chiffré. Bento4 prend comme entrée le contenu mp4 non chiffré.
seo-description: Nous utilisons à la fois le gestionnaire de package Bento4 et le gestionnaire de package hors ligne Adobe pour créer du contenu DASH chiffré. Bento4 prend comme entrée le contenu mp4 non chiffré.
seo-title: Assemblage de votre contenu avec Bento4
title: Assemblage de votre contenu avec Bento4
uuid: 88323a4e-d0b5-4a41-acec-7126d3e0c90b
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Mise en package de contenu pour Windows et PlayReady {#package-for-widevine}

Nous utilisons à la fois le gestionnaire de package Bento4 et le gestionnaire de package hors ligne Adobe pour créer du contenu DASH chiffré. Bento4 prend comme entrée le contenu mp4 non chiffré.

## Assemblage de votre contenu avec Bento4{#package-your-content-with-bento}

Le gestionnaire Bento4 s’attend à ce que l’entrée mp4 soit préfragmentée. La distribution Bento4 Packager inclut un outil pour cela.

**Appel de Bento4**

Les appels typiques de l’emballeur Bento4 ressemblent aux exemples suivants :

    ./mp4dash
    -f
    —use-segment-
    —use-segment-timeline
    —subtitles—encry-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd 09fc0747c7c5ac215b3b
    —widevine
    
    —widevine-header=provider:intertrust#content_id:2a &quot;CC_300_640x360.mp4&quot;-o &quot;CC_300_640x366 0_DASH&quot;
    
>
    ./mp4dash
    -f
    —use-segment-
    —use-segment-timeline
    —subtitles—encry-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd 09fc0747c7c5ac215b3b
    —playready
    
    —playready-header=\&quot;LA_URL:http://pr.test.expressplay.com/playready/RightsManager.asmx\&quot;

L’exemple ci-dessous combine les schémas PlayReady et Widevine. Dans ce cas particulier, le gestionnaire de package ajoute les données d’initialisation de protection de contenu Widevine et de protection de contenu PlayReady au contenu DASH de sortie.

    /mp4dash
    -f
    —use-segment-
    —use-segment-timeline
    —subtitles—encry-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd 09fc0747c7c5ac215b3b
    —playready
    
    —playready-header=\&quot;LA_URL:http://pr.test.expressplay.com/playready/RightsManager.asmx\&quot;—widevine—widevine-header=provider:intertrust#content_id:2a &quot;CC_300_640x360.mp4&quot;o &quot;CC_300_640x360_DASH&quot;où
    
    
    
    
    

La valeur de l’ `--encryption-key` indicateur se trouve dans le formulaire `<base16 encoded key id>:<base16 encoded encryption key>`.

L’ `--widevine-header=provider:intertrust#content_id:2a` indicateur indique au gestionnaire de package d’inclure la zone Pssh dans le manifeste, dont TVSDK a actuellement besoin pour la lecture.
La valeur de `-playready-header` est pour l’acquisition de la licence PlayReady.

## Assemblage de votre contenu avec Adobe Offline Packager {#package-your-content-with-adobe-offline-packager}

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