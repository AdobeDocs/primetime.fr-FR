---
description: La définition de l’interface de diffusion publicitaire du lecteur vidéo (VPAID) fournit une interface commune pour lire des publicités vidéo. VPAID offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux cible les publicités, de suivre les impressions publicitaires et de monétiser le contenu vidéo.
title: Configuration requise pour les publicités personnalisées
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# Exigences d&#39;annonces personnalisées {#custom-ad-requirements}

Le lecteur TVSDK peut lire des publicités VPAID (Digital Video Player Ad-Interface Definition) et afficher l’état de chargement des publicités. En cas d’erreur dans la publicité ou de chargement trop long des publicités, TVSDK ignore ces publicités.

La définition de l’interface de diffusion publicitaire du lecteur vidéo (VPAID) fournit une interface commune pour lire des publicités vidéo. VPAID offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux cible les publicités, de suivre les impressions publicitaires et de monétiser le contenu vidéo.

<!--<a id="section_9A358902CBC24999BA34206EE2029616"></a>-->

TVSDK prend en charge les fonctionnalités suivantes :

* Version 1.0 et 2.0 de la spécification VPAID
* Publicités VPAID linéaires sur du contenu vidéo à la demande (VOD)
* Publicités VPAID Flash

   Les publicités VPAID doivent être basées sur un Flash et la réponse publicitaire doit identifier le type de média de la publicité VPAID comme `application/x-shockwave-flash`.

Les fonctionnalités suivantes ne sont pas prises en charge :

* Publicités non linéaires, telles que les publicités superposées et les publicités complémentaires dynamiques
* Prévisualisation de publicités VPAID
* Publicités VPAID dans du contenu en direct
* Publicités VPAID JavaScript

## État du chargement {#section_5F55C0101CD44A65BCFE1D124CBDF239}

TVSDK distribue les événements suivants :

* `AdLoading`
* `AdLoaded`
* `AdStarted`
* `AdPlaying`
* `AdStopped`

Après le événement `AdStopped`, TVSDK reprend le contenu vidéo.

>[!TIP]
>
>Si vous spécifiez la valeur zéro, TVSDK tente de charger la publicité jusqu’à ce qu’elle se charge ou qu’une erreur se produise.

## Publicités {#section_3EA452F420884335AE90DF23C17E416A} ignorées

Si le chargement de la publicité est trop long ou qu’il y a des erreurs dans la publicité, TVSDK peut ignorer la publicité et la publicité suivante dans la capsule est lue automatiquement.

Si le paramètre `AuditudeSettings.customAdLoadTimeout` spécifie un nombre de secondes supérieur à zéro, TVSDK tente de charger la publicité pendant la durée spécifiée. S’il ne parvient pas à charger la publicité, celle-ci est ignorée. Par exemple, si vous configurez `AuditudeSettings.customAdLoadTimeout:5`, TVSDK tente de charger la publicité pendant un maximum de 5 secondes. Si la publicité ne se charge toujours pas, elle est ignorée.
