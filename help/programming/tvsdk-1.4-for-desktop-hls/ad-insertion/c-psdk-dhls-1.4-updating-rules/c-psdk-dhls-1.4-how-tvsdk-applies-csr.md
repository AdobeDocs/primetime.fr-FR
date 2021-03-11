---
title: Application des règles de sélection créative
description: Application des règles de sélection créative
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# Application des règles de sélection créative{#applying-creative-selection-rules}

TVSDK applique les règles de sélection créative de la manière suivante :

* TVSDK applique d’abord toutes les règles `default`, suivies des règles spécifiques à la zone.
* TVSDK ignore toutes les règles qui ne sont pas définies pour l’identifiant de zone actuel.
* Une fois que TVSDK applique les règles par défaut, les règles spécifiques à une zone peuvent modifier davantage les priorités créatives en fonction des correspondances `host` (domaine) sur le créatif sélectionné par les règles `default`.

* Dans le fichier d’exemples de règles inclus avec des règles de zone supplémentaires, une fois que TVSDK applique les règles `default`, si le domaine créatif M3U8 ne contient pas [!DNL my.domain.com] ou [!DNL a.bcd.com] et que la zone publicitaire est `1234`, les éléments créatifs sont réorganisés et le créatif VPAID Flash lu en premier s’il est disponible. Dans le cas contraire, une publicité MP4 est lue, et ainsi de suite jusqu’à JavaScript.

* Si un créatif publicitaire est sélectionné et que TVSDK ne peut pas être lu en mode natif ( [!DNL .mp4], [!DNL .flv], etc.), TVSDK émet une demande de reconditionnement.

Notez que les types d’annonces qui peuvent être gérés par TVSDK sont toujours définis par le paramètre `validMimeTypes` dans `AuditudeSettings`.
