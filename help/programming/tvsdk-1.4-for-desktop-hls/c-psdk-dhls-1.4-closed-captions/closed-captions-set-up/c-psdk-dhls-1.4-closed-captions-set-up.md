---
description: Le sous-titrage codé affiche la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que la visionneuse est difficile à entendre.
title: Utilisation de sous-titres fermés
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Utilisation de sous-titres fermés{#work-with-closed-captions}

Le sous-titrage codé affiche la partie audio d’une vidéo sous forme de texte à l’écran lorsque le son est inaudible ou que la visionneuse est difficile à entendre.

Les sous-titres codés sont généralement dans la même langue que l’audio et affichent également des sons en arrière-plan sous forme de texte, mais les sous-titres sont généralement dans une langue différente et n’incluent pas de sons en arrière-plan.

TVSDK prend en charge le rendu des formats suivants :

* Sous-titrage 608 et 708, lorsqu’il est diffusé dans le cadre du flux de transport vidéo via HLS sous la forme de paquets de données dans des flux vidéo MPEG-2.
* Les fichiers de sous-titres WebVTT, qui sont référencés à partir des fichiers de manifeste M3U8, tels que définis dans les spécifications HLS. Elles sont automatiquement disponibles sous forme de suivi de sous-titres dans le lecteur Primetime.

Vous pouvez :

* Sélectionnez un suivi de légende disponible pour le suivi actuel et écoutez les événements qui indiquent d’autres suivi disponibles.
* Activez ou désactivez le sous-titrage codé (visible ou non) à l’aide de l’option `MediaPlayer` .
* Sélectionnez les options de style qui déterminent le mode de rendu des sous-titres fermés par le moteur vidéo sous-jacent. Utilisez la variable `MediaPlayerItem` pour sélectionner des formats tels que la police ou la couleur de la police.
