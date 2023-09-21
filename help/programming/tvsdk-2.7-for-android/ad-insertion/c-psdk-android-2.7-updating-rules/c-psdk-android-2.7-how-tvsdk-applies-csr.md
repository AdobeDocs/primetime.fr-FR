---
keywords: règles de sélection créative;AdobeTVSDKConfig
title: Appliquer les règles de sélection créative
description: Appliquer les règles de sélection créative
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Appliquer les règles de sélection créative {#apply-creative-selection-rules}

TVSDK applique les règles de sélection créative de la manière suivante :

* TVSDK applique toutes les `default` d’abord, suivies des règles spécifiques à la zone.
* TVSDK ignore les règles qui ne sont pas définies pour l’identifiant de zone actuel.
* Une fois que TVSDK applique les règles par défaut, les règles spécifiques aux zones peuvent modifier davantage les priorités de création en fonction de la variable `host` (domaine) correspond à l’élément créatif sélectionné par l’événement `default` règles.

* Dans le fichier d’exemple de règles inclus avec des règles de zone supplémentaires, une fois que TVSDK applique la variable `default` règles, si le domaine créatif M3U8 ne contient pas [!DNL my.domain.com] ou [!DNL a.bcd.com] et la zone publicitaire est `1234`, les créatifs sont réorganisés et le créatif VPAID Flash est lu en premier s’il est disponible. Sinon, une publicité MP4 est lue, et ainsi de suite, sur JavaScript.

* Si un créatif publicitaire est sélectionné, TVSDK ne peut pas être lu en mode natif ( [!DNL .mp4], [!DNL .flv], etc.), TVSDK émet une demande de reconditionnement.

Notez que les types d’annonces qui peuvent être gérés par TVSDK sont toujours définis via la variable `validMimeTypes` définition dans `AuditudeSettings`.

<!-- 

In Android 2.5 API docs, I see a 
<span class="codeph"> setValidMimeTypes</span> but not a 
<span class="codeph"> getValidMimeTypes</span>.

 -->
