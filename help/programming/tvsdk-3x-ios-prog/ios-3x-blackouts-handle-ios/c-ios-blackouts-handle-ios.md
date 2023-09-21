---
description: TVSDK gère les coupures d’accès dans les diffusions vidéo en direct et fournit du contenu alternatif en cas de panne.
title: Gestion des coupures de courant
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Gestion des coupures de courant {#handle-blackouts}

TVSDK gère les coupures d’accès dans les diffusions vidéo en direct et fournit du contenu alternatif en cas de panne.

Le cas d’utilisation le plus courant associé à un blackout de programmation se produit lorsque l’application de votre lecteur fournit un contenu alternatif aux utilisateurs qui ne sont pas éligibles pour regarder la diffusion principale. Cette application peut utiliser TVSDK pour déterminer le début et la fin de la période de blackout. Ainsi, au début de la période de blackout, la lecture peut passer de la diffusion principale à une diffusion alternative, puis revenir à la diffusion principale lorsque la période de blackout est terminée.

Pour mettre en oeuvre la solution pour ce cas pratique :

1. Configurez votre application pour vous abonner à des balises de blackout dans un manifeste de diffusion en direct.

   TVSDK n’est pas directement conscient des balises de blackout, mais il permet à votre application de s’abonner aux notifications lorsque des balises spécifiques sont rencontrées lors de l’analyse du fichier manifeste.
1. Ajout d’un écouteur de notification pour `PTTimedMetadataChangedNotification`.

   Cette notification est envoyée chaque fois qu’une balise inscrite est analysée dans le manifeste, et qu’une nouvelle `PTTimedMetadata` est préparé à partir de celle-ci.

1. Mettez en oeuvre une méthode d’écouteur, telle que `onMediaPlayerSubscribedTagIdentified`, pour `PTTimedMetadata` au premier plan.

1. Chaque fois qu’une mise à jour est effectuée au cours de la lecture, utilisez la variable `PTMediaPlayerTimeChangeNotification` listener à gérer `PTTimedMetadata` objets.

1. Ajoutez la variable `PTTimedMetadata` gestionnaire.

   Ce gestionnaire vous permet de basculer vers un autre contenu et de revenir au contenu principal, comme indiqué par le `PTTimedMetadata` et son temps de lecture.

1. Utilisation `onSubscribedTagInBackground` pour mettre en oeuvre la méthode listener pour `PTTimedMetadata` en arrière-plan.

   Cette méthode surveille le minutage du flux en arrière-plan, ce qui vous permet de déterminer quand vous pouvez passer d’un contenu alternatif au contenu principal.

1. Mettez en oeuvre une méthode d’écouteur pour les erreurs d’arrière-plan.
1. Si la plage d’interruption se trouve dans le répertoire de stockage global de documents (DVR) du flux de lecture, mettez à jour les plages impraticables.

   Votre application doit définir la plage non consultable dans le répertoire de stockage global de documents dans les cas suivants :

   * Lorsqu’il rejoint la diffusion principale lorsqu’une panne se produit dans le répertoire de stockage global de documents (DVR).
   * Lorsque vous revenez au contenu principal à partir du contenu alternatif.
