---
description: Ce guide fournit des informations sur la manière de développer des applications de lecteur vidéo à l’aide de TVSDK pour Android, qui est mis en oeuvre dans Java.
title: Présentation du produit, audience et ce guide
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# Présentation {#audience}

Ce guide fournit des informations sur la manière de développer des applications de lecteur vidéo à l’aide de TVSDK pour Android, qui est mis en oeuvre dans Java.

<!--<a id="section_FC24E86A2E6442B8A3769160769BBDFA"></a>-->

* Pour obtenir la liste des fonctionnalités prises en charge par TVSDK, voir [Fonctionnalités de Primetime TVSDK](../../../tvsdk-3x-android-prog/android-3x-introduction/overview-prod-audience-guide/android-3x-overview-of-the-player.md).
* Pour connaître la configuration matérielle et logicielle requise pour l’utilisation de TVSDK, voir [Conditions](../../../tvsdk-3x-android-prog/android-3x-introduction/android-3x-requirements.md).
* Pour obtenir la liste des API disponibles, voir [API Android TVSDK](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.5/index.html).

## Présentation du produit {#section_9664959F25C948878F2F7EF3D360CA95}

TVSDK comprend des descriptions d’API et des exemples de code pour vous aider à intégrer des fonctionnalités vidéo, de protection de contenu et de publicité avancées à votre lecteur. Vous utilisez Java pour créer une interface utilisateur de lecteur vidéo. TVSDK permet de connecter cette interface utilisateur à son lecteur multimédia. Vous pouvez ainsi lire des vidéos et de la publicité en fonction de manifestes multimédia. Vous pouvez également utiliser TVSDK pour récupérer des informations sur la vidéo, gérer la sécurité et contrôler et surveiller la lecture.

## Audience {#section_527860B373734D3BA89FCF5EC1F6DC37}

Ce guide suppose que vous comprenez comment développer des applications et des lecteurs vidéo à l’aide de Java. Vous mettez en oeuvre l’interface utilisateur de votre lecteur vidéo en Java et incorporez les fonctionnalités TVSDK dont vous avez besoin.

## À propos de ce guide {#section_9A5B2FC506B34B5DB71CA827B307A4D0}

Ce guide fournit des informations qui vous permettent d’incorporer des fonctionnalités TVSDK dans un lecteur vidéo à l’aide de Java sur les appareils Android.

## Notation d’espace de noms dans ce guide {#section_8B866054E9ED4B5F99DCA7A681404632}

>[!TIP]
>
>Préfixe d’espace de noms de l’API TVSDK [!DNL com.adobe.mediacore] est souvent omis pour des raisons de concision.
>
>De nombreux éléments d’API sont référencés sans leur désignateur de classe parent si le contexte est clair.
