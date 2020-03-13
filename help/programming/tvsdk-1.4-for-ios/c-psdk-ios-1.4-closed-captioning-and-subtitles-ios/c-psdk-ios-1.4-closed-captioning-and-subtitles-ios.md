---
description: Les sous-titres et les sous-titres codés présentent des différences uniques et vous les activez de différentes manières.
seo-description: Les sous-titres et les sous-titres codés présentent des différences uniques et vous les activez de différentes manières.
seo-title: Sous-titres et sous-titres
title: Sous-titres et sous-titres
uuid: 91daf0be-087a-4be5-86c2-f8b83da43a8f
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Conditions requises pour les sous-titres et les sous-titres codés {#requirements-for-subtitles-and-closed-captions}

Les sous-titres et les sous-titres codés présentent des différences uniques et vous les activez de différentes manières.

Les flux de sous-titres s’exécutent en parallèle avec le contenu principal. Les sous-titres codés font partie des paquets de données des flux vidéo MPEG-2.

Vous devez connaître les exigences suivantes pour les sous-titres et sous-titres fermés :

* **Sous-titres**

   * Les sous-titres codés sont généralement dans la même langue que le son et représentent également les sons d’arrière-plan comme du texte.
   * Les sous-titres codés font partie des paquets de données des flux vidéo MPEG-2 dans le flux de transmission vidéo.
   * Les sous-titres codés sont pris en charge dans la mesure prévue par le cadre de la Fondation AV.

* **Sous-titres**

   * Les sous-titres sont généralement rédigés dans une autre langue et n’incluent pas de sons en arrière-plan.
   * Les sous-titres se trouvent dans des flux qui s’exécutent en parallèle avec le contenu principal.

      Le `PTMediaPlayer` lecteur lit le contenu et les publicités principaux, où le contenu principal peut être en direct/linéaire ou VOD, et les publicités peuvent être preroll, mid-roll ou post-roll.
   Voici quelques autres conditions requises pour les sous-titres dans iOS :

   * Pour les horodatages, la `X-TIMESTAMP-MAP` valeur, spécifiée dans la section d’en-tête du `WebVTT` fichier, doit correspondre à l’horodatage vidéo.

   * Pour le système, vous devez utiliser iOS 6.1 ou version ultérieure.


>[!IMPORTANT]
>
>Les exigences relatives aux sous-titres ne s’appliquent pas aux sous-titres codés.

