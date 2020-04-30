---
description: La chronologie de la publicité appropriée à une lecture de contenu VOD peut être inappropriée pour les lectures suivantes. Vous pouvez remplacer une chronologie VOD sans modifier le contenu.
seo-description: La chronologie de la publicité appropriée à une lecture de contenu VOD peut être inappropriée pour les lectures suivantes. Vous pouvez remplacer une chronologie VOD sans modifier le contenu.
seo-title: Modifications apportées à VOD
title: Modifications apportées à VOD
uuid: e734aacd-b42e-4c8e-a16a-c7a0739a0492
translation-type: tm+mt
source-git-commit: ''

---


# Modifications apportées à VOD {#changes-to-vod}

La chronologie de la publicité appropriée à une lecture de contenu VOD peut être inappropriée pour les lectures suivantes. Vous pouvez remplacer une chronologie VOD sans modifier le contenu.

Les situations dans lesquelles vous souhaitez peut-être remplacer une chronologie VOD sont les suivantes :

* Remplacez les annonces locales, mais laissez les annonces nationales pendant une fenêtre C3.
* Remplacez les publicités incorporées après la fermeture de la fenêtre C3.
* Remplacez dynamiquement les anciennes publicités C3 par des publicités plus récentes de plus longue durée.
* Insérez moins de publicités ou aucune du tout.

Vous pouvez remplacer la chronologie de la publicité en envoyant une nouvelle demande d&#39;insertion de publicité avec le fichier M3U8 d&#39;origine et une autre valeur du paramètre de `pttimeline` requête.