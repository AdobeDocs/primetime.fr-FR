---
description: Nous utilisons le packager Bento4 et le packager hors ligne Adobe pour créer du contenu DASH chiffré. Bento4 prend comme entrée du contenu mp4 non chiffré.
title: Regroupez votre contenu avec Bento4
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Modules de contenu pour Windows et PlayReady {#package-for-widevine}

Nous utilisons le packager Bento4 et le packager hors ligne Adobe pour créer du contenu DASH chiffré. Bento4 prend comme entrée du contenu mp4 non chiffré.

## Regroupez votre contenu avec Bento4{#package-your-content-with-bento}

Le packager Bento4 s’attend à ce que le mp4 d’entrée soit préfragmenté. La distribution de packager Bento4 comprend un outil pour cela.

**Appel de Bento4**

Les appels types de packager Bento4 ressemblent aux exemples ci-dessous :

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

L’exemple ci-dessous combine des schémas PlayReady et Widevine. Dans ce cas particulier, le programme de package ajoute à la fois les données d’initialisation de protection de contenu Windows et PlayReady au contenu DASH de sortie.

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

La valeur de la variable `--encryption-key` L’indicateur se trouve dans le formulaire `<base16 encoded key id>:<base16 encoded encryption key>`.

La variable `--widevine-header=provider:intertrust#content_id:2a` L’indicateur indique au module d’inclure la boîte push dans le manifeste, dont TVSDK a actuellement besoin pour la lecture.

La valeur de `-playready-header` est destiné à l’acquisition de la licence PlayReady .

## Regroupez votre contenu avec Adobe Offline Packager {#package-your-content-with-adobe-offline-packager}

Adobe Offline Packager prend comme entrée du contenu mp4 non chiffré.

**Appel de Adobe Offline Packager**

Un appel type d’adobe offline packager ressemble à l’appel ci-dessous :

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

Dans ce cas particulier, le programme de package hors ligne ajoute les données d’initialisation de protection de contenu Windows et PlayReady au contenu DASH de sortie. La valeur de `-key_file_path` est pour une clé codée en base64. La valeur de `-playready_LA_URL` est destiné à l’acquisition de la licence PlayReady .

L’argument conf_path pointe vers un fichier de configuration qui contiendra les éléments suivants :

```
<config>
<frag_dur>4</frag_dur>
<target_dur>6</target_dur>
<encrypt_audio>false</encrypt_audio>
</config>
```

Comme certains appareils Android — principalement Amazon Fire TV — ne prennent pas en charge le décryptage audio, le chiffrement audio est facultatif.
