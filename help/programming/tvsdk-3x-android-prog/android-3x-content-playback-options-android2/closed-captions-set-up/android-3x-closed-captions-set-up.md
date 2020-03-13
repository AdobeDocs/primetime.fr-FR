---
description: Le sous-titrage affiche la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que le lecteur est malentendant.
seo-description: Le sous-titrage affiche la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que le lecteur est malentendant.
seo-title: Utilisation de sous-titres
title: Utilisation de sous-titres
uuid: d7860de4-2881-4817-a4cc-5e7ab557a1db
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Présentation {#work-with-closed-captions-overview}

Le sous-titrage affiche la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que le lecteur est malentendant.

Les sous-titres sont généralement dans la même langue que l’audio et affichent également des sons en arrière-plan sous forme de texte, mais les sous-titres sont généralement dans une autre langue et n’incluent pas de sons en arrière-plan.

TVSDK prend en charge le rendu des formats suivants :

* 608 et 708 sous-titrage, lorsqu’ils sont distribués dans le flux de transport vidéo sur HLS sous forme de paquets de données dans les flux vidéo MPEG-2.
* Les fichiers de sous-titrage WebVTT, qui sont référencés à partir des fichiers de manifeste M3U8, tels que définis dans les spécifications HLS.

   Ces fichiers sont automatiquement disponibles sous forme de pistes de sous-titrage dans le lecteur Primetime.

Vous pouvez effectuer les opérations suivantes :

* Sélectionnez une piste de sous-titrage disponible pour être la piste actuelle et écoutez les  de qui indiquent d’autres pistes disponibles.
* Activez (visible) ou désactivez (invisible) le sous-titrage à l’aide de l’ `MediaPlayer` interface.
* Sélectionnez des options de style qui déterminent le mode de rendu des sous-titres par le moteur vidéo sous-jacent.

   Utilisez l’ `MediaPlayerItem` interface pour sélectionner des formats tels que la police ou la couleur de la police.