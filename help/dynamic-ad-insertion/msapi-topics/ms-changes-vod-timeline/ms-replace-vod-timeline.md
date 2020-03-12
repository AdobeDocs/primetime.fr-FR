---
description: La chronologie de la publicité appropriée à une lecture de contenu VOD peut être inappropriée pour les lectures suivantes. Vous pouvez remplacer une chronologie VOD sans modifier le contenu.
seo-description: La chronologie de la publicité appropriée à une lecture de contenu VOD peut être inappropriée pour les lectures suivantes. Vous pouvez remplacer une chronologie VOD sans modifier le contenu.
seo-title: Changements dans VOD
title: Changements dans VOD
uuid: e734aacd-b42e-4c8e-a16a-c7a0739a0492
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Changements dans VOD {#changes-to-vod}

La chronologie de la publicité appropriée à une lecture de contenu VOD peut être inappropriée pour les lectures suivantes. Vous pouvez remplacer une chronologie VOD sans modifier le contenu.

Les situations dans lesquelles vous souhaitez peut-être remplacer une chronologie VOD sont les suivantes :

* Remplacez les annonces locales, mais laissez les annonces nationales pendant une fenêtre C3.
* Remplacez les publicités intégrées après la fermeture de la fenêtre C3.
* Remplacez dynamiquement les anciennes publicités C3 par des annonces plus récentes de plus longue durée.
* Insérez moins de publicités ou aucune publicité du tout.

Vous pouvez remplacer le plan de montage chronologique de la publicité en envoyant une nouvelle demande d’insertion de publicité avec le fichier M3U8 d’origine et une autre valeur du paramètre `pttimeline` .