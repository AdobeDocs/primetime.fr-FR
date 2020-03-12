---
description: Remplacez une chronologie VOD par l’envoi d’une nouvelle demande d’insertion d’annonce au serveur de manifeste par un paramètre de de chronologie de journal correctement défini.
seo-description: Remplacez une chronologie VOD par l’envoi d’une nouvelle demande d’insertion d’annonce au serveur de manifeste par un paramètre de de chronologie de journal correctement défini.
seo-title: Remplacement d’une chronologie VOD
title: Remplacement d’une chronologie VOD
uuid: 17a6daa3-5ee5-48fb-8981-0d183aed0fe4
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Remplacement d’une chronologie VOD {#replace-a-vod-timeline}

Remplacez une chronologie VOD par l’envoi d’une nouvelle demande d’insertion d’annonce au serveur de manifeste par un paramètre de de chronologie de journal correctement défini.

1. Préparez une demande d’insertion d’annonce de la manière habituelle.
1. Définissez le paramètre `ptcueformat` du sur DPIScte35.
1. Définissez le paramètre  `enableC3` sur true ou false selon le cas.
1. Créez un `pttimeline` paramètre à l’aide du format de chronologie VOD :
   1. Spécifiez chaque bloc de contenu (chapitre) avec `duration = 0` et `number_of_lots = 1`.
   1. Spécifiez chaque bloc publicitaire comme vous le faites habituellement, mais définissez cette option `lots = 0` pour supprimer une coupure. Définissez cette option `duration = 0` pour utiliser la durée de la coupure publicitaire (à partir du fichier M3U8).

## Exemple : Remplacement d’une chronologie VOD

Cet exemple suppose que le contenu VOD est conforme `Original.m3u8` à une chronologie de `C,120,1;B,60,2,m;C,120,1;B,60,2,m;C,120,1;`

La demande de serveur de manifeste suivante remplace les sauts par un pré-roll de 30 secondes `Original.m3u8` suivi de deux sauts de durée de deux minutes chacun.

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,120,4,m;C,0,1;B,120,4,m;C,0,1;
```

La demande de serveur de manifeste suivante supprime les sauts d’accès `Original.m3u8` et ajoute un pré-roll de 30 secondes et un post-roll de 30 secondes.

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,0,0,m;C,0,1;B,0,0,m;C,0,1;B,30,2,t;
```
