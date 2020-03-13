---
description: La définition de l’interface d’administration des publicités du lecteur vidéo (VPAID) fournit une interface commune pour lire des publicités vidéo. VPAID offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.
seo-description: La définition de l’interface d’administration des publicités du lecteur vidéo (VPAID) fournit une interface commune pour lire des publicités vidéo. VPAID offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.
seo-title: Conditions requises pour les publicités personnalisées
title: Conditions requises pour les publicités personnalisées
uuid: 6d4ba87b-ffe5-467d-8ab5-9795928c2f69
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Conditions requises pour les publicités personnalisées {#custom-ad-requirements}

Le lecteur TVSDK peut lire des annonces VPAID (Ad-Interface Definition) du lecteur vidéo numérique et afficher l’état de chargement de la publicité. En cas d’erreurs dans la publicité ou si le chargement des publicités est trop long, TVSDK ignore ces publicités.

La définition de l’interface d’administration des publicités du lecteur vidéo (VPAID) fournit une interface commune pour lire des publicités vidéo. VPAID offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo.

<!--<a id="section_9A358902CBC24999BA34206EE2029616"></a>-->

Le kit TVSDK prend en charge les fonctionnalités suivantes :

* Version 1.0 et 2.0 de la spécification VPAID
* Annonces VPAID linéaires sur du contenu vidéo à la demande (VOD)
* Publicités VPAID Flash

   Les publicités VPAID doivent être basées sur Flash et la réponse de la publicité doit identifier le type de média de la publicité VPAID comme `application/x-shockwave-flash`étant.

Les fonctionnalités suivantes ne sont pas prises en charge :

* Publicités non linéaires, telles que les publicités superposées et les publicités complémentaires dynamiques
* Préchargement de publicités VPAID
* Publicités VPAID dans du contenu en direct
* Publicités VPAID JavaScript

## Chargement de l’état {#section_5F55C0101CD44A65BCFE1D124CBDF239}

Le TVSDK distribue le  suivant :

* `AdLoading`
* `AdLoaded`
* `AdStarted`
* `AdPlaying`
* `AdStopped`

Une fois le `AdStopped` terminé, le kit TVSDK reprend le contenu vidéo.

>[!TIP]
>
>Si vous spécifiez la valeur zéro, TVSDK tente de charger la publicité jusqu’à ce qu’elle se charge ou qu’une erreur se produise.

## Ignorer les publicités {#section_3EA452F420884335AE90DF23C17E416A}

Si le chargement de la publicité est trop long ou qu’il y a des erreurs dans la publicité, le kit TVSDK peut ignorer la publicité et la publicité suivante dans la capsule est lue automatiquement.

Si le `AuditudeSettings.customAdLoadTimeout` paramètre spécifie un nombre de secondes supérieur à zéro, le kit TVSDK tente de charger la publicité pendant la durée spécifiée. S’il ne parvient pas à charger la publicité, celle-ci est ignorée. Par exemple, si vous configurez `AuditudeSettings.customAdLoadTimeout:5`, le kit TVSDK tente de charger la publicité pendant 5 secondes au maximum. Si la publicité ne se charge toujours pas, elle est ignorée.
