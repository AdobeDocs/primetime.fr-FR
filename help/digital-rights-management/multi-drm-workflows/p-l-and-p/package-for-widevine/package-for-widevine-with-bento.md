---
description: Nous utilisons à la fois le packager Bento4 et le packager hors ligne Adobe pour créer du contenu chiffré DASH. Bento4 prend comme entrée du contenu mp4 non chiffré.
seo-description: Nous utilisons à la fois le packager Bento4 et le packager hors ligne Adobe pour créer du contenu chiffré DASH. Bento4 prend comme entrée du contenu mp4 non chiffré.
seo-title: Assemblage de votre contenu avec Bento4
title: Assemblage de votre contenu avec Bento4
uuid: 88323a4e-d0b5-4a41-acec-7126d3e0c90b
translation-type: tm+mt
source-git-commit: 75702ea2a524d7b38bb9ac83cb094c8482b1098f
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# Mise en package de contenu pour Windows et PlayReady {#package-for-widevine}

Nous utilisons à la fois le packager Bento4 et le packager hors ligne Adobe pour créer du contenu chiffré DASH. Bento4 prend comme entrée du contenu mp4 non chiffré.

## Assemblage de votre contenu avec Bento4{#package-your-content-with-bento}

Le conditionneur Bento4 s&#39;attend à ce que l&#39;entrée mp4 soit préfragmentée. La distribution Bento4 packager inclut un outil pour cela.

**Appel de Bento4**

Les invocations typiques de Bento4 packager ressemblent aux exemples ci-dessous :

```
./mp4dash
-f
--use-segment-list
--use-segment-timeline
--subtitles
--encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
--widevine
--widevine-header=provider:intertrust#content_id:2a "CC_300_640x360.mp4"
-o "CC_300_640x360_DASH"
```

```
./mp4dash
-f
--use-segment-list
--use-segment-timeline
--subtitles
--encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
--playready
--playready-header=\"LA_URL:http://pr.test.expressplay.com/playready/RightsManager.asmx\"
```

L&#39;exemple ci-dessous combine les schémas PlayReady et Widevine. Dans ce cas particulier, l’outil de création de package ajoute les données d’initialisation de protection de contenu Widevine et de protection de contenu PlayReady au contenu DASH de sortie.

```
/mp4dash
-f
--use-segment-list
--use-segment-timeline
--subtitles
--encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
--playready
--playready-header=\"LA_URL:http://pr.test.expressplay.com/playready/RightsManager.asmx\"
--widevine
--widevine-header=provider:intertrust#content_id:2a "CC_300_640x360.mp4"
-o "CC_300_640x360_DASH"
```

where

La valeur de l’ `--encryption-key` indicateur se présente sous la forme `<base16 encoded key id>:<base16 encoded encryption key>`.

L’ `--widevine-header=provider:intertrust#content_id:2a` indicateur indique à l’outil de création de package d’inclure la zone de message dans le manifeste, dont TVSDK a actuellement besoin pour la lecture.

La valeur de `-playready-header` est pour l’acquisition de la licence PlayReady.

## Assemblage de votre contenu avec Adobe Offline Packager {#package-your-content-with-adobe-offline-packager}

Adobe Offline Packager prend comme entrée du contenu mp4 non chiffré.

**Appel d&#39;Adobe Hors ligne Packager**

Un appel standard d’adobe offline packager ressemblerait à l’appel ci-dessous :

```
java -jar OfflinePackager.jar -conf_path Content_PR_WV.xml -in_path "Jaigo.mp4"
-out_path "Jaigo_DASH"
-key_file_path "Jaigo_DASH/_info/key.B64.random"
-widevine_key_id c595f214d84dc7ecf31a8ebf1b7ddda5
-widevine_provider intertrust
-playready_LA_URL
http://pr.test.expressplay.com/playready/RightsManager.asmx
-playready_keyid c595f214d84dc7ecf31a8ebf1b7ddda5
-content_id c595f214d84dc7ecf31a8ebf1b7ddda5
```

Dans ce cas particulier, le gestionnaire de package hors ligne ajoute les données d&#39;initialisation de protection de contenu Widevine et de protection de contenu PlayReady au contenu DASH de sortie. La valeur de `-key_file_path` est pour une clé codée en base 64. La valeur de `-playready_LA_URL` est pour l’acquisition de la licence PlayReady.

L&#39;argument conf_path pointe vers un fichier de configuration qui contiendra les éléments suivants :

```
<config>
<frag_dur>4</frag_dur>
<target_dur>6</target_dur>
<encrypt_audio>false</encrypt_audio>
</config>
```

Certains périphériques Android, principalement Amazon Fire TV, ne prenant pas en charge le déchiffrement audio, le chiffrement audio est facultatif.
