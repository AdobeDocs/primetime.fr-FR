---
description: Les objets MediaPlayerNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.
seo-description: Les objets MediaPlayerNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.
seo-title: Notifications pour l’état du lecteur, le  , les erreurs et la journalisation
title: Notifications pour l’état du lecteur, le  , les erreurs et la journalisation
uuid: 7ce5bed0-f312-437e-a82f-b1d4a8e1926c
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Présentation {#notifications-for-player-status-activity-errors-and-logging-overview}

Les objets MediaPlayerNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.

Votre application peut récupérer la notification et les informations d’état. Vous pouvez également créer un système de journalisation pour les diagnostics et la validation à l’aide des informations de notification.

Vous implémentez des écouteurs  pour capturer et répondre aux  de. De nombreux  fournissent des notifications `MediaPlayerNotification` d’état.