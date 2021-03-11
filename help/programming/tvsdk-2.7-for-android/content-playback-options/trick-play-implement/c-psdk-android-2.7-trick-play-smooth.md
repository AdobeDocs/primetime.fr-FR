---
description: Si votre système a accès au décodage assisté par le matériel, vous pouvez obtenir un jeu plus fluide qu’avec la mise en oeuvre logicielle pure de TVSDK en utilisant le format iFrame.
title: Opérations de jeux de ficelles plus fluides
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---


# Opérations de lecture de l&#39;astuce plus fluides {#smoother-trick-play-operations}

Si votre système a accès au décodage assisté par le matériel, vous pouvez obtenir un jeu plus fluide qu’avec la mise en oeuvre logicielle pure de TVSDK en utilisant le format iFrame.

<!--<a id="section_3DBFD7A3D1C7453096D3D3885E786263"></a>-->

L’utilisation du format iFrame entraîne des opérations de lecture par astuces qui ne sont pas lisses. Une opération de lecture plus fluide utilise un profil normal (et non iFrame), la prise en charge du décodage matériel et une cadence accrue. Différents périphériques de décodage assistés par le matériel ont des capacités différentes. La vitesse du doublon nécessite 60 images par seconde (i/s) et la vitesse quadruple requiert 120 i/s.

>[!IMPORTANT]
>
>Adobe recommande de limiter la lecture à la vitesse de doublon pour les périphériques Android plus récents et de ne pas utiliser cette fonctionnalité pour les périphériques Android plus anciens.

Pour obtenir un jeu plus fluide, définissez `ABRControlParameters.maxPlayoutRate` sur le multiple souhaité de vitesse normale (par exemple, 2.0 pour la vitesse de doublon). Si un appel suivant à `MediaPlayer.setRate()` comporte un argument inférieur ou égal à la valeur que vous avez définie pour `maxPlayoutRate`, TVSDK utilise un profil normal pour obtenir une lecture plus fluide. Sinon, il utilise un profil iFrame pour l’opération de trickplay.
