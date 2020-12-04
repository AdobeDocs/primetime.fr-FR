---
description: TVSDK gère les coupures d’électricité dans les flux vidéo en direct et fournit du contenu alternatif lors d’une coupure d’Internet.
seo-description: TVSDK gère les coupures d’électricité dans les flux vidéo en direct et fournit du contenu alternatif lors d’une coupure d’Internet.
seo-title: Gestion des pannes de courant en direct
title: Gestion des pannes de courant en direct
uuid: 1f70a272-bc77-4d41-a999-b076cb42ac5e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Gérer les pannes de courant en direct {#handle-blackouts-in-live-streams}

TVSDK gère les coupures d’électricité dans les flux vidéo en direct et fournit du contenu alternatif lors d’une coupure d’Internet.

Le cas d’utilisation le plus courant associé à une coupure de programmation est lorsque votre application de lecteur fournit un autre contenu aux utilisateurs qui ne sont pas éligibles pour regarder le flux principal. Cette application peut utiliser TVSDK pour déterminer le début et la fin de la période de coupure. Ainsi, au début de la période d’interruption, la lecture peut passer du flux principal à un flux alternatif, puis revenir au flux principal lorsque la période d’interruption est terminée.

Pour mettre en oeuvre la solution pour ce cas d’utilisation :

1. Configurez votre application pour vous abonner à des balises d’arrêt dans un manifeste de flux en direct.

   TVSDK n’est pas directement conscient des balises d’arrêt, mais il permet à votre application de s’abonner à des notifications lorsque des balises spécifiques sont rencontrées lors de l’analyse des fichiers de manifeste.
1. Ajoutez un écouteur de notification pour `PTTimedMetadataChangedNotification`.

   Cette notification est envoyée chaque fois qu’une balise abonnée est analysée dans le manifeste et qu’une nouvelle balise `PTTimedMetadata` est préparée à partir de celle-ci.

1. Mettez en oeuvre une méthode d’écouteur, telle que `onMediaPlayerSubscribedTagIdentified`, pour les objets `PTTimedMetadata` au premier plan.

1. Chaque fois qu’une mise à jour est effectuée au cours de la lecture, utilisez l’écouteur `PTMediaPlayerTimeChangeNotification` pour gérer les objets `PTTimedMetadata`.

1. Ajoutez le gestionnaire `PTTimedMetadata`.

   Ce gestionnaire vous permet de passer à un autre contenu et de revenir au contenu principal comme indiqué par l’objet `PTTimedMetadata` et son temps de lecture.

1. Utilisez `onSubscribedTagInBackground` pour implémenter la méthode d’écouteur pour les objets `PTTimedMetadata` en arrière-plan.

   Cette méthode surveille le timing du flux d’arrière-plan, ce qui vous permet de déterminer à quel moment vous pouvez revenir d’un autre contenu au contenu principal.

1. Implémentez une méthode d’écouteur pour les erreurs d’arrière-plan.
1. Si la plage d’interruption se trouve dans le DVR du flux de lecture, mettez à jour les plages impossibles à rechercher.

   Dans les cas suivants, votre application doit définir la plage non recherchée dans le DVR :

   * Lorsqu&#39;on rejoint le flux principal lorsqu&#39;une panne est survenue dans le magnétoscope numérique.
   * Lorsque vous revenez au contenu principal à partir du contenu alternatif.

