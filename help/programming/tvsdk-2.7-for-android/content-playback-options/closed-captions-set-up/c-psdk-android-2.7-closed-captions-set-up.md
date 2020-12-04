---
description: Le sous-titrage permet d’afficher la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que le lecteur est malentendant.
seo-description: Le sous-titrage permet d’afficher la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que le lecteur est malentendant.
seo-title: Utilisation de sous-titres fermés
title: Utilisation de sous-titres fermés
uuid: 6e105316-a166-45c1-b6b0-70c89c97c297
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---


# Aperçu {#work-with-closed-captions-overview}

Le sous-titrage permet d’afficher la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que le lecteur est malentendant.

Les sous-titres sont généralement dans la même langue que l’audio et affichent également des sons d’arrière-plan sous forme de texte, mais les sous-titres sont généralement dans une autre langue et n’incluent pas de sons d’arrière-plan.

TVSDK prend en charge le rendu des formats suivants :

* 608 et 708 sous-titrage, lorsqu&#39;ils sont diffusés dans le flux de transport vidéo sur HLS sous forme de paquets de données dans les flux vidéo MPEG-2.
* Les fichiers de sous-titrage WebVTT, qui sont référencés à partir des fichiers de manifeste M3U8 définis dans les spécifications HLS.

   Ces fichiers sont automatiquement disponibles en tant que pistes de sous-titrage dans le lecteur Primetime.

Vous pouvez effectuer les opérations suivantes :

* Sélectionnez une piste de sous-titrage disponible pour être la piste actuelle et écoutez les événements qui indiquent d&#39;autres pistes disponibles.
* Activez (visible) ou désactivez (invisible) le sous-titrage à l’aide de l’interface `MediaPlayer`.
* Sélectionnez des options de mise en forme qui déterminent le mode de rendu des sous-titres par le moteur vidéo sous-jacent.

   Utilisez l&#39;interface `MediaPlayerItem` pour sélectionner des formats tels que la police ou la couleur de la police.

