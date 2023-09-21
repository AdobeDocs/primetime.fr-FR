---
description: Remplacez une chronologie VOD en envoyant une nouvelle requête d’insertion de publicités au serveur de manifeste avec un paramètre de requête de chronologie correctement défini.
title: Remplacement d’une chronologie VOD
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# Remplacement d’une chronologie VOD {#replace-a-vod-timeline}

Remplacez une chronologie VOD en envoyant une nouvelle requête d’insertion de publicités au serveur de manifeste avec un paramètre de requête de chronologie correctement défini.

1. Préparez une requête d’insertion de publicités de la manière habituelle.
1. Définissez la variable `ptcueformat` paramètre de requête sur DPIScte35.
1. Définissez la variable `enableC3` le paramètre de requête doit être true ou false, selon le cas.
1. Créez un `pttimeline` à l’aide du format de frise chronologique VOD :
   1. Spécifiez chaque bloc de contenu (chapitre) avec `duration = 0` et `number_of_lots = 1`.
   1. Spécifiez chaque bloc d’annonce comme vous le faites habituellement, mais définissez `lots = 0` pour supprimer un saut. Définir `duration = 0` pour utiliser la durée de la coupure publicitaire (à partir du fichier M3U8).

## Exemple : remplacement d’une chronologie VOD

Cet exemple suppose que le contenu VOD se trouve dans `Original.m3u8` avec une chronologie de `C,120,1;B,60,2,m;C,120,1;B,60,2,m;C,120,1;`

La requête de serveur de manifeste suivante remplace les sauts dans `Original.m3u8` avec un preroll de 30 secondes, suivi de deux pauses de deux minutes chacune.

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,120,4,m;C,0,1;B,120,4,m;C,0,1;
```

La requête de serveur de manifeste suivante supprime les coupures dans `Original.m3u8` et ajoute un preroll de 30 secondes et un post-roll de 30 secondes.

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,0,0,m;C,0,1;B,0,0,m;C,0,1;B,30,2,t;
```
