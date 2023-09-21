---
description: Les objets MediaPlayerNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.
title: Notifications d’état, d’activité, d’erreurs et de journalisation du lecteur
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%

---

# Présentation {#notifications-for-player-status-activity-errors-and-logging-overview}

Les objets MediaPlayerNotification fournissent des informations sur les modifications de l’état du lecteur, les avertissements et les erreurs. Les erreurs qui arrêtent la lecture de la vidéo entraînent également un changement de l’état du lecteur.

Votre application peut récupérer les informations de notification et d’état. Vous pouvez également créer un système de journalisation pour les diagnostics et la validation à l’aide des informations de notification.

Vous implémentez des écouteurs d’événements pour capturer les événements et y répondre. De nombreux événements fournissent des `MediaPlayerNotification` notifications d’état.
