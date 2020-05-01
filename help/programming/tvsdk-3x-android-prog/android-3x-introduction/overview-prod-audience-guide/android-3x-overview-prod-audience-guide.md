---
description: Ce guide explique comment développer des applications de lecteurs vidéo en utilisant TVSDK pour Android, qui est mis en oeuvre en Java.
seo-description: Ce guide explique comment développer des applications de lecteurs vidéo en utilisant TVSDK pour Android, qui est mis en oeuvre en Java.
seo-title: Présentation du produit, audience et ce guide
title: Présentation du produit, audience et ce guide
uuid: dd281a3e-a85f-4470-a730-2c5e87d0e490
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

---


# Présentation {#audience}

Ce guide explique comment développer des applications de lecteurs vidéo en utilisant TVSDK pour Android, qui est mis en oeuvre en Java.

<!--<a id="section_FC24E86A2E6442B8A3769160769BBDFA"></a>-->

* Pour une liste des fonctionnalités prises en charge par TVSDK, voir Fonctionnalités [de TVSDK](../../../tvsdk-3x-android-prog/android-3x-introduction/overview-prod-audience-guide/android-3x-overview-of-the-player.md)Primetime.
* Pour connaître la configuration matérielle et logicielle requise pour l’utilisation de TVSDK, voir [Exigences](../../../tvsdk-3x-android-prog/android-3x-introduction/android-3x-requirements.md).
* Pour obtenir une liste des API disponibles, voir API [Android](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.5/index.html)TVSDK.

## Présentation du produit {#section_9664959F25C948878F2F7EF3D360CA95}

TVSDK comprend des descriptions d’API et des exemples de code pour vous aider à intégrer des fonctionnalités vidéo avancées, la protection du contenu et les fonctionnalités publicitaires dans votre lecteur. Vous utilisez Java pour créer une interface utilisateur de lecteur vidéo. TVSDK vous permet de connecter cette interface utilisateur à son lecteur multimédia. Cela vous permet de lire des vidéos et des publicités basées sur des manifestes médiatiques. Vous pouvez également utiliser TVSDK pour récupérer des informations sur la vidéo, gérer la sécurité et contrôler et surveiller la lecture.

## Audience {#section_527860B373734D3BA89FCF5EC1F6DC37}

Ce guide suppose que vous comprenez comment développer des applications et des lecteurs vidéo à l’aide de Java. Vous mettez en oeuvre l’interface utilisateur de votre lecteur vidéo en Java et incorporez les fonctionnalités TVSDK dont vous avez besoin.

## A propos de ce guide {#section_9A5B2FC506B34B5DB71CA827B307A4D0}

Ce guide fournit des informations qui vous permettent d’incorporer des fonctionnalités TVSDK dans un lecteur vidéo à l’aide de Java sur les périphériques Android.

## Notation des Espaces de nommage dans ce guide {#section_8B866054E9ED4B5F99DCA7A681404632}

>[!TIP]
>
>Le préfixe d’espace de nommage de l’API TVSDK [!DNL com.adobe.mediacore] est souvent omis pour des raisons de concision.
>
>De nombreux éléments d’API sont référencés sans leur indicateur de classe parent si le contexte est clair.