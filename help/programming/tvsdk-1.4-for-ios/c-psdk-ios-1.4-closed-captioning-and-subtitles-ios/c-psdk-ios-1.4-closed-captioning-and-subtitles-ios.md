---
description: Les sous-titres codés présentent des différences uniques et vous pouvez les activer de différentes manières.
title: Sous-titres et sous-titres codés
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Conditions requises pour les sous-titres et les sous-titres non intégrés {#requirements-for-subtitles-and-closed-captions}

Les sous-titres codés présentent des différences uniques et vous pouvez les activer de différentes manières.

Les flux de sous-titres s’exécutent en parallèle avec le contenu principal. Les sous-titres codés font partie des paquets de données des flux vidéo MPEG-2.

Vous devez tenir compte des exigences suivantes pour les sous-titres et sous-titres fermés :

* **Sous-titres codés**

   * Les sous-titres codés sont généralement dans la même langue que l’audio et représentent également des sons d’arrière-plan sous forme de texte.
   * Les sous-titres codés font partie des paquets de données des flux vidéo MPEG-2 dans le flux de transmission vidéo.
   * Les sous-titres codés sont pris en charge dans la mesure fournie par le framework AV Foundation.

* **Sous-titres**

   * Les sous-titres sont généralement rédigés dans une autre langue et n’incluent pas de sons en arrière-plan.
   * Les sous-titres se trouvent dans des flux qui s’exécutent en parallèle avec le contenu principal.

     La variable `PTMediaPlayer` lit le contenu et les publicités principaux, où le contenu principal peut être en direct/linéaire ou VOD, et les publicités peuvent être preroll, mid-roll ou post-roll.

  Voici quelques exigences supplémentaires pour les sous-titres dans iOS :

   * Pour les horodatages, la variable `X-TIMESTAMP-MAP` , qui est spécifiée dans la section d’en-tête de la variable `WebVTT` doit correspondre à l’horodatage vidéo.

   * Pour le système, vous devez utiliser iOS 6.1 ou version ultérieure.

>[!IMPORTANT]
>
>Les exigences relatives aux sous-titres ne s’appliquent pas aux sous-titres non intégrés.
