---
description: Le sous-titrage permet d’afficher la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que le lecteur est malentendant.
seo-description: Le sous-titrage permet d’afficher la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que le lecteur est malentendant.
seo-title: Utilisation de sous-titres fermés
title: Utilisation de sous-titres fermés
uuid: 881266aa-3c32-4035-9547-0f363949f77b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Utilisation de sous-titres fermés{#work-with-closed-captions}

Le sous-titrage permet d’afficher la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que le lecteur est malentendant.

Les sous-titres sont généralement dans la même langue que l’audio et affichent également des sons d’arrière-plan sous forme de texte, mais les sous-titres sont généralement dans une autre langue et n’incluent pas de sons d’arrière-plan.

TVSDK prend en charge le rendu des formats suivants :

* 608 et 708 sous-titrage, lorsqu&#39;ils sont diffusés dans le flux de transport vidéo sur HLS sous forme de paquets de données dans les flux vidéo MPEG-2.
* Les fichiers de sous-titrage WebVTT, qui sont référencés à partir des fichiers de manifeste M3U8 définis dans les spécifications HLS. Ils sont automatiquement disponibles en tant que pistes de sous-titrage dans le lecteur Primetime.

Vous pouvez :

* Sélectionnez une piste de sous-titrage disponible pour être la piste actuelle et écoutez les événements qui indiquent d&#39;autres pistes disponibles.
* Activez ou désactivez le sous-titrage (visible ou non visible) à l’aide de l’ `MediaPlayer` interface.
* Sélectionnez des options de mise en forme qui déterminent le mode de rendu des sous-titres par le moteur vidéo sous-jacent. Utilisez l’ `MediaPlayerItem` interface pour sélectionner des formats tels que la police ou la couleur de la police.

