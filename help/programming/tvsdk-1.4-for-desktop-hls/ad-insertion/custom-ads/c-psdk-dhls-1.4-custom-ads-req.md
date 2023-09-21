---
description: La définition de l’interface de diffusion publicitaire du lecteur vidéo (VPAID) fournit une interface commune pour lire des publicités vidéo. VPAID offre une expérience multimédia riche aux utilisateurs et permet aux éditeurs de mieux cibler les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.
title: Exigences publicitaires personnalisées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Exigences publicitaires personnalisées {#custom-ad-requirements}

Le lecteur TVSDK peut lire des publicités VPAID (définition d’interface publicitaire du lecteur vidéo numérique) et afficher l’état de chargement de la publicité. En cas d’erreur dans la publicité ou si le chargement des publicités prend trop de temps, TVSDK ignore ces publicités.

La définition de l’interface de diffusion publicitaire du lecteur vidéo (VPAID) fournit une interface commune pour lire des publicités vidéo. VPAID offre une expérience multimédia riche aux utilisateurs et permet aux éditeurs de mieux cibler les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.

<!--<a id="section_9A358902CBC24999BA34206EE2029616"></a>-->

TVSDK prend en charge les fonctionnalités suivantes :

* Version 1.0 et 2.0 de la spécification VPAID
* Publicités VPAID linéaires sur le contenu vidéo à la demande (VOD)
* Publicités VPAID Flash

  Les publicités VPAID doivent être basées sur des Flashs et la réponse publicitaire doit identifier le type de média de la publicité VPAID comme `application/x-shockwave-flash`.

Les fonctionnalités suivantes ne sont pas prises en charge :

* Publicités non linéaires telles que les publicités superposées et les publicités compagnons dynamiques
* Préchargement des publicités VPAID
* Publicités VPAID dans du contenu en direct
* Publicités JavaScript VPAID

## État du chargement {#section_5F55C0101CD44A65BCFE1D124CBDF239}

TVSDK distribue les événements suivants :

* `AdLoading`
* `AdLoaded`
* `AdStarted`
* `AdPlaying`
* `AdStopped`

Après la `AdStopped` , le TVSDK reprend le contenu vidéo.

>[!TIP]
>
>Si vous spécifiez une valeur nulle, TVSDK tente de charger la publicité jusqu’à ce qu’elle se charge ou qu’une erreur se produise.

## Ignorer les publicités {#section_3EA452F420884335AE90DF23C17E416A}

Si le chargement de la publicité prend trop de temps ou qu’elle comporte des erreurs, TVSDK peut ignorer la publicité et la publicité suivante dans la capsule est automatiquement lue.

Si la variable `AuditudeSettings.customAdLoadTimeout` spécifie un nombre de secondes supérieur à zéro, TVSDK tente de charger la publicité pendant la durée spécifiée. S’il ne parvient pas à charger la publicité, celle-ci est ignorée. Par exemple, si vous configurez `AuditudeSettings.customAdLoadTimeout:5`, TVSDK tente de charger la publicité pendant un maximum de 5 secondes. Si la publicité ne se charge toujours pas, elle est ignorée.
