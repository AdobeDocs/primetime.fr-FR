---
description: La chronologie publicitaire appropriée à une lecture de contenu VOD peut être inappropriée pour les lectures suivantes. Vous pouvez remplacer une chronologie VOD sans modifier le contenu.
title: Modifications apportées à VOD
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---


# Modifications apportées à VOD {#changes-to-vod}

La chronologie publicitaire appropriée à une lecture de contenu VOD peut être inappropriée pour les lectures suivantes. Vous pouvez remplacer une chronologie VOD sans modifier le contenu.

Voici les situations dans lesquelles vous pouvez souhaiter remplacer une chronologie VOD :

* Remplacez les publicités locales, mais laissez les publicités nationales pendant une fenêtre C3.
* Remplacez les publicités brûlées après la fermeture de la fenêtre C3.
* Remplacez dynamiquement les anciennes publicités C3 par des publicités plus récentes de plus longue durée.
* Insérez moins de publicités ou aucune publicité du tout.

Vous pouvez remplacer la chronologie de la publicité en envoyant une nouvelle demande d’insertion de publicités avec le fichier M3U8 d’origine et une autre valeur de la variable `pttimeline` paramètre de requête.