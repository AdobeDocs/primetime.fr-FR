---
description: Vous pouvez remplacer le comportement par défaut de la recherche de TVSDK par rapport aux publicités lors de l’utilisation de marqueurs d’annonce personnalisés.
title: Contrôle du comportement de lecture pour la recherche sur les marqueurs publicitaires personnalisés
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Contrôle du comportement de lecture pour la recherche sur les marqueurs publicitaires personnalisés{#control-playback-behavior-for-seeking-over-custom-ad-markers}

Vous pouvez remplacer le comportement par défaut de la recherche de TVSDK par rapport aux publicités lors de l’utilisation de marqueurs d’annonce personnalisés.

Par défaut, lorsqu’un utilisateur effectue une recherche dans ou dans des sections publicitaires antérieures résultant du placement de marqueurs publicitaires personnalisés, TVSDK ignore les publicités. Il peut s’agir d’une différence par rapport au comportement de lecture actuel pour les coupures publicitaires standard.

Vous pouvez indiquer à TVSDK de repositionner le curseur de lecture au début de la dernière publicité personnalisée ignorée lorsque l’utilisateur effectue une recherche au-delà d’une ou de plusieurs publicités personnalisées.

1. Configurez une instance de métadonnées à l’aide de la méthode `DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` énumération définie sur la valeur de chaîne &quot;true&quot; (et non en tant que booléen) `true`).

1. Création et configuration d’une `MediaResource` instance, transmission des options de configuration supplémentaires à `TimeRangeCollection.toMetadata`. Cette méthode reçoit des options de configuration supplémentaires via une autre structure de métadonnées générique.
