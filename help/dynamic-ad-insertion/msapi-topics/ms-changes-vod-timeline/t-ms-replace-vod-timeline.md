---
description: Remplacez une chronologie VOD en envoyant une nouvelle demande d’insertion de publicité au serveur de manifeste par un paramètre de requête pttimeline correctement défini.
seo-description: Remplacez une chronologie VOD en envoyant une nouvelle demande d’insertion de publicité au serveur de manifeste par un paramètre de requête pttimeline correctement défini.
seo-title: Remplacement d’une chronologie VOD
title: Remplacement d’une chronologie VOD
uuid: 17a6daa3-5ee5-48fb-8981-0d183aed0fe4
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---


# Remplace la chronologie VOD {#replace-a-vod-timeline}

Remplacez une chronologie VOD en envoyant une nouvelle demande d’insertion de publicité au serveur de manifeste par un paramètre de requête pttimeline correctement défini.

1. Préparez une demande d’insertion d’annonce de la manière habituelle.
1. Définissez le paramètre de requête `ptcueformat` sur DPIScte35.
1. Définissez le paramètre de requête `enableC3` sur true ou false selon le cas.
1. Créez un paramètre `pttimeline` à l’aide du format de chronologie VOD :
   1. Spécifiez chaque bloc de contenu (chapitre) avec `duration = 0` et `number_of_lots = 1`.
   1. Spécifiez chaque bloc publicitaire comme vous le faites habituellement, mais définissez `lots = 0` pour supprimer une coupure. Définissez `duration = 0` pour utiliser la durée des coupures publicitaires (à partir du fichier M3U8).

## Exemple : Remplacement d’une chronologie VOD

Cet exemple suppose que le contenu VOD est dans `Original.m3u8` avec une chronologie de `C,120,1;B,60,2,m;C,120,1;B,60,2,m;C,120,1;`

La demande de serveur de manifeste suivante remplace les sauts dans `Original.m3u8` par un pré-roulement de 30 secondes, suivi de deux sauts de durée de deux minutes chacun.

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,120,4,m;C,0,1;B,120,4,m;C,0,1;
```

La demande de serveur de manifeste suivante supprime les sauts dans `Original.m3u8` et ajoute un pré-roll de 30 secondes et un post-roll de 30 secondes.

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,0,0,m;C,0,1;B,0,0,m;C,0,1;B,30,2,t;
```
