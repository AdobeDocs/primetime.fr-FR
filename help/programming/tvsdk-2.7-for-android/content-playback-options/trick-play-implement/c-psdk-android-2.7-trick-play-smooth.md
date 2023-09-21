---
description: Si votre système a accès au décodage assisté par le matériel, vous pouvez effectuer un jeu plus fluide qu’avec la mise en oeuvre pure du TVSDK logiciel au format iFrame.
title: Opérations de lecture des astuces plus fluides
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# Opérations de lecture des astuces plus fluides {#smoother-trick-play-operations}

Si votre système a accès au décodage assisté par le matériel, vous pouvez effectuer un jeu plus fluide qu’avec la mise en oeuvre pure du TVSDK logiciel au format iFrame.

<!--<a id="section_3DBFD7A3D1C7453096D3D3885E786263"></a>-->

L’utilisation du format iFrame entraîne des opérations de lecture de trucage qui ne sont pas lisses. L’opération de lecture de l’astuce utilise un profil normal (et non un iFrame), la prise en charge du décodage matériel et une fréquence d’image accrue. Différents appareils de décodage assistés par le matériel ont des fonctionnalités différentes. La vitesse double nécessite 60 images par seconde (i/s) et la vitesse quadruple nécessite 120 i/s.

>[!IMPORTANT]
>
>Adobe recommande de limiter la lecture à une vitesse double pour les appareils Android plus récents et de ne pas utiliser cette fonctionnalité pour les appareils Android plus anciens.

Pour obtenir une lecture plus fluide, définissez `ABRControlParameters.maxPlayoutRate` au multiple souhaité de vitesse normale (par exemple, 2.0 pour une vitesse double). Si un appel ultérieur à `MediaPlayer.setRate()` comporte un argument inférieur ou égal à la valeur définie pour `maxPlayoutRate`, TVSDK utilise un profil normal pour obtenir une lecture plus fluide. Dans le cas contraire, il utilise un profil iFrame pour l’opération de trickplay.
