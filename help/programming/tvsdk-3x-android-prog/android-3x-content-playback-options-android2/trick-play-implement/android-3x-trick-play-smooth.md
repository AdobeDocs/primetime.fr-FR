---
description: Si votre système a accès au décodage assisté par le matériel, vous pouvez obtenir un jeu plus fluide qu’avec la mise en oeuvre logicielle pure de TVSDK en utilisant le format iFrame.
seo-description: Si votre système a accès au décodage assisté par le matériel, vous pouvez obtenir un jeu plus fluide qu’avec la mise en oeuvre logicielle pure de TVSDK en utilisant le format iFrame.
seo-title: Opérations de jeux de ficelles plus fluides
title: Opérations de jeux de ficelles plus fluides
uuid: 959d6c67-b64f-4666-8de7-54d247459fd1
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Opérations de jeux de ficelles plus fluides {#smoother-trick-play-operations}

Si votre système a accès au décodage assisté par le matériel, vous pouvez obtenir un jeu plus fluide qu’avec la mise en oeuvre logicielle pure de TVSDK en utilisant le format iFrame.

<!--<a id="section_3DBFD7A3D1C7453096D3D3885E786263"></a>-->

L’utilisation du format iFrame entraîne des opérations de lecture par astuces qui ne sont pas lisses. Une opération de lecture plus fluide utilise un profil normal (et non iFrame), la prise en charge du décodage matériel et une cadence accrue. Différents périphériques de décodage assistés par le matériel ont des capacités différentes. La vitesse du Doublon nécessite 60 images par seconde (i/s) et la vitesse quadruple requiert 120 i/s.

>[!IMPORTANT]
>
>Adobe recommande de limiter la lecture à la vitesse de doublon pour les périphériques Android plus récents et de ne pas utiliser cette fonctionnalité pour les périphériques Android plus anciens.

Pour obtenir un jeu plus fluide, définissez `ABRControlParameters.maxPlayoutRate` sur le multiple souhaité de vitesse normale (par exemple, 2.0 pour la vitesse de doublon). Si un appel ultérieur à `MediaPlayer.setRate()` comporte un argument inférieur ou égal à la valeur que vous définissez pour `maxPlayoutRate`, TVSDK utilise un profil normal pour obtenir une lecture plus fluide. Sinon, il utilise un profil iFrame pour l’opération de trickplay.