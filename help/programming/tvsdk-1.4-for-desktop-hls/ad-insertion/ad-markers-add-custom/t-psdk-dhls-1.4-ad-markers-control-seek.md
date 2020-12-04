---
description: Vous pouvez remplacer le comportement par défaut de la recherche de TVSDK par rapport aux publicités lors de l’utilisation de marqueurs publicitaires personnalisés.
seo-description: Vous pouvez remplacer le comportement par défaut de la recherche de TVSDK par rapport aux publicités lors de l’utilisation de marqueurs publicitaires personnalisés.
seo-title: Contrôler le comportement de lecture pour la recherche sur les marques publicitaires personnalisées
title: Contrôler le comportement de lecture pour la recherche sur les marques publicitaires personnalisées
uuid: 926299c6-9c23-457d-b836-08432e4e169e
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Contrôler le comportement de lecture pour la recherche sur les marques publicitaires personnalisées{#control-playback-behavior-for-seeking-over-custom-ad-markers}

Vous pouvez remplacer le comportement par défaut de la recherche de TVSDK par rapport aux publicités lors de l’utilisation de marqueurs publicitaires personnalisés.

Par défaut, lorsqu’un utilisateur effectue des recherches dans ou après des sections d’annonces résultant de l’emplacement de marques publicitaires personnalisées, TVSDK ignore les publicités. Ceci peut différer du comportement de lecture actuel pour les pauses publicitaires standard.

Vous pouvez indiquer à TVSDK de repositionner le curseur de lecture au début de la dernière publicité personnalisée ignorée lorsque l’utilisateur effectue une recherche au-delà d’une ou de plusieurs publicités personnalisées.

1. Configurez une instance de métadonnées dont la énumération `DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` est définie sur la valeur de chaîne &quot;true&quot; (et non sur une valeur booléenne `true`).

1. Créez et configurez une instance `MediaResource`, en transmettant les options de configuration supplémentaires à `TimeRangeCollection.toMetadata`. Cette méthode reçoit des options de configuration supplémentaires via une autre structure de métadonnées générique.

