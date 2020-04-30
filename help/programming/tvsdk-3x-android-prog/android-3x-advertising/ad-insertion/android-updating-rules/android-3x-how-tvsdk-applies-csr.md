---
description: 'null'
keywords: creative selection rules;AdobeTVSDKConfig
seo-description: 'null'
seo-title: Appliquer les règles de sélection créative
title: Appliquer les règles de sélection créative
uuid: 66e55f95-25ce-4838-b222-63ee34e535d1
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# Appliquer les règles de sélection créative {#apply-creative-selection-rules}

TVSDK applique les règles de sélection créative de la manière suivante :

* TVSDK applique d’abord toutes les `default` règles, puis les règles spécifiques à chaque zone.
* TVSDK ignore toutes les règles qui ne sont pas définies pour l’identifiant de zone actuel.
* Une fois que TVSDK applique les règles par défaut, les règles spécifiques à la zone peuvent modifier davantage les priorités créatives en fonction des `host` (domaine) correspondant à la création sélectionnée par les `default` règles.

* Dans le fichier d’exemples de règles inclus avec des règles de zone supplémentaires, une fois que TVSDK applique les `default` règles, si le domaine créatif M3U8 ne contient pas `my.domain.com` ou `a.bcd.com` et que la zone publicitaire est `1234`définie, les éléments créatifs sont réorganisés et le fichier créatif Flash VPAID est lu en premier si disponible. Dans le cas contraire, une publicité MP4 est lue, et ainsi de suite jusqu’à JavaScript.

* Si un créatif publicitaire est sélectionné et que TVSDK ne peut pas être lu en mode natif ( [!DNL .mp4], [!DNL .flv], etc.), TVSDK émet une demande de reconditionnement.

Notez que les types d’annonces qui peuvent être gérés par TVSDK sont toujours définis par le `validMimeTypes` paramètre de la section `AuditudeSettings`.

<!-- 

In Android 2.5 API docs, I see a 
<span class="codeph"> setValidMimeTypes</span> but not a 
<span class="codeph"> getValidMimeTypes</span>.

 -->

