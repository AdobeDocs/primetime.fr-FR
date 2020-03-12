---
description: 'null'
keywords: creative selection rules;AdobeTVSDKConfig
seo-description: 'null'
seo-title: Appliquer les règles de sélection créative
title: Appliquer les règles de sélection créative
uuid: 313306b7-6b99-4d90-8717-2b0a1e39a07b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Appliquer les règles de sélection créative{#apply-creative-selection-rules}

TVSDK applique les règles de sélection créative de différentes manières :

* TVSDK applique d’abord toutes les `default` règles, puis les règles spécifiques à chaque zone.
* TVSDK ignore toutes les règles qui ne sont pas définies pour l’identifiant de zone actuel.
* Une fois que TVSDK applique les règles par défaut, les règles spécifiques à une zone peuvent modifier davantage les priorités créatives en fonction des correspondances `host` (domaine) sur le créatif sélectionné par les `default` règles.

* Dans le fichier d’exemples de règles inclus avec des règles de zone supplémentaires, une fois que TVSDK applique les `default` règles, si le domaine créatif M3U8 ne contient pas [!DNL my.domain.com] ou [!DNL a.bcd.com] et que la zone publicitaire est `1234`définie, les créatifs sont réorganisés et le créatif Flash VPAID est lu en premier si disponible. Dans le cas contraire, une publicité MP4 est lue, et ainsi de suite jusqu’à JavaScript.

* Si un créatif publicitaire est sélectionné et que TVSDK ne peut pas être lu en mode natif ( [!DNL .mp4], [!DNL .flv], etc.), TVSDK émet une demande de reconditionnement.

Notez que les types de publicité qui peuvent être gérés par TVSDK sont toujours définis par le `validMimeTypes` paramètre de `AuditudeSettings`.
