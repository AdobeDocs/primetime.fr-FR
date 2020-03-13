---
description: Vous pouvez enregistrer la position de lecture actuelle dans une vidéo et reprendre la lecture à la même position dans une session ultérieure.
seo-description: Vous pouvez enregistrer la position de lecture actuelle dans une vidéo et reprendre la lecture à la même position dans une session ultérieure.
seo-title: Enregistrer la position de la vidéo et reprendre ultérieurement
title: Enregistrer la position de la vidéo et reprendre ultérieurement
uuid: 03ed5c63-008d-4dd1-9a31-baefa73b56e2
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Enregistrer la position de la vidéo et reprendre ultérieurement{#save-the-video-position-and-resume-later}

Vous pouvez enregistrer la position de lecture actuelle dans une vidéo et reprendre la lecture à la même position dans une session ultérieure.

Les publicités insérées dynamiquement diffèrent d’une session utilisateur à l’autre. Par conséquent, l’enregistrement de la position **avec** les publicités épissées fait référence à une position différente dans une session ultérieure. TVSDK fournit des méthodes pour récupérer la position de lecture tout en ignorant les publicités épissées.

1. Lorsque l’utilisateur ferme une vidéo, votre application récupère et enregistre la position dans la vidéo.

   >[!TIP]
   >
   >Les durées des publicités ne sont pas incluses.

   Les coupures publicitaires peuvent varier dans chaque session en raison des modèles publicitaires, du plafonnement des fréquences, etc. L’heure actuelle de la vidéo dans une session peut être différente dans une session ultérieure. Lors de l’enregistrement d’une position dans la vidéo, l’application récupère l’heure locale. Utilisez la `localTime` propriété pour lire cette position que vous pouvez enregistrer sur le périphérique ou dans une base de données sur le serveur.

   ```
   var resumeTime:Number = player.localTime; 
   // save the resumeTime to a persistent location
   ```

   Si, par exemple, l’utilisateur se trouve à la 20e minute de la vidéo et que cette position comprend cinq minutes de publicités, `currentTime` 1 200 secondes s’écouleront `be` , alors qu’à cette position, `localTime` `be` 900 secondes s’écouleront.

1. Restaurez la session utilisateur lorsque le lecteur  le  reprend.

   TVSDK ne reprend pas la lecture entre les initialisations TVSDK, car il n’enregistre aucune information localement. Votre application doit implémenter cette logique.

   ```
   // retrieve the resumeTime from the persistent location 
   var resumeTime:Number:Number = ...;
   ```

1. Pour reprendre la vidéo à la même position :

   * Pour reprendre la lecture de la vidéo à partir de la position enregistrée lors d’une session précédente, utilisez `seekToLocal`.

      >[!TIP]
      >
      >Cette méthode est appelée uniquement avec des valeurs d’heure locale. Si la méthode est appelée avec les résultats de l’heure actuelle, un comportement incorrect se produit.

   * Pour atteindre l’heure actuelle, utilisez `seek`.

1. Lorsque votre application reçoit le  de modification de l’ `onStatusChanged` état, recherchez l’heure locale enregistrée.
1. Fournissez les coupures publicitaires comme spécifié dans l’interface de la stratégie publicitaire.
1. Implémentez un sélecteur de stratégie d’annonce personnalisée en étendant le sélecteur de stratégie d’annonce par défaut.
1. Fournissez les coupures publicitaires qui doivent être présentées à l’utilisateur par implémentation `selectAdBreaksToPlay`.

   Lorsque le lecteur entre dans l’état PRÉPARÉ, toutes les publicités sont déjà résolues. La `AdPolicyInfo.adBreakTimelineItem` propriété contient donc toutes les coupures publicitaires avant la position de l’heure locale. Votre application peut décider de lire une coupure publicitaire preroll et de reprendre à l’heure locale spécifiée, de lire une coupure publicitaire mid-roll et de reprendre à l’heure locale spécifiée, ou de ne pas lire de coupures publicitaires.
