---
description: Si votre système a accès au décodage assisté par le matériel, vous pouvez obtenir un jeu plus fluide qu’avec la mise en oeuvre du logiciel pur TVSDK en utilisant le format iFrame.
seo-description: Si votre système a accès au décodage assisté par le matériel, vous pouvez obtenir un jeu plus fluide qu’avec la mise en oeuvre du logiciel pur TVSDK en utilisant le format iFrame.
seo-title: Lissage des opérations de jeu par astuce
title: Lissage des opérations de jeu par astuce
uuid: 4749bfa0-17bf-4444-a167-987249945325
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Lissage des opérations de jeu par astuce {#smoother-trick-play-operations}

Si votre système a accès au décodage assisté par le matériel, vous pouvez obtenir un jeu plus fluide qu’avec la mise en oeuvre du logiciel pur TVSDK en utilisant le format iFrame.

<!--<a id="section_3DBFD7A3D1C7453096D3D3885E786263"></a>-->

L’utilisation du format iFrame génère des opérations de lecture de l’astuce qui ne sont pas fluides. Une opération de lecture de l’astuce plus fluide utilise une  normale (et non un iFrame), la prise en charge du décodage matériel et une fréquence d’images accrue. Différents périphériques de décodage assistés par le matériel possèdent des fonctionnalités différentes. La vitesse  exige 60 images par seconde (i/s) et une vitesse quadruple (120 i/s).

>[!IMPORTANT]
>
>Adobe recommande de limiter la lecture à la vitesse  pour les périphériques Android plus récents et de ne pas utiliser cette fonctionnalité pour les périphériques Android plus anciens.

Pour obtenir un jeu plus fluide, définissez `ABRControlParameters.maxPlayoutRate` sur le multiple souhaité de la vitesse normale (par exemple, 2,0 pour la vitesse ). Si un appel ultérieur à `MediaPlayer.setRate()` comporte un argument inférieur ou égal à la valeur que vous avez définie pour `maxPlayoutRate`, TVSDK utilise un  normal pour obtenir une lecture plus fluide. Sinon, il utilise un d’iFrame pour l’opération de superposition.
