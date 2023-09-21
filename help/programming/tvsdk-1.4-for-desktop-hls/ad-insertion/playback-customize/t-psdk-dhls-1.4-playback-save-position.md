---
description: Vous pouvez enregistrer la position de lecture actuelle dans une vidéo et reprendre la lecture à la même position dans une session ultérieure.
title: Enregistrer la position de la vidéo et reprendre ultérieurement
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# Enregistrer la position de la vidéo et reprendre ultérieurement{#save-the-video-position-and-resume-later}

Vous pouvez enregistrer la position de lecture actuelle dans une vidéo et reprendre la lecture à la même position dans une session ultérieure.

Les publicités insérées dynamiquement diffèrent d’une session utilisateur à l’autre, ce qui permet d’enregistrer la position. **avec** les publicités épissées font référence à une position différente dans une session ultérieure. TVSDK fournit des méthodes pour récupérer la position de lecture tout en ignorant les publicités épissées.

1. Lorsque l’utilisateur quitte une vidéo, votre application récupère et enregistre la position dans la vidéo.

   >[!TIP]
   >
   >Les durées des publicités ne sont pas incluses.

   Les coupures publicitaires peuvent varier au cours de chaque session en raison des schémas publicitaires, de la limitation de fréquence, etc. L’heure actuelle de la vidéo dans une session peut être différente dans une session ultérieure. Lors de l’enregistrement d’une position dans la vidéo, l’application récupère l’heure locale . Utilisez la variable `localTime` pour lire cette position que vous pouvez enregistrer sur le périphérique ou dans une base de données sur le serveur.

   ```
   var resumeTime:Number = player.localTime; 
   // save the resumeTime to a persistent location
   ```

   Par exemple, si l’utilisateur se trouve à la 20e minute de la vidéo et que cette position inclut cinq minutes de publicités, `currentTime` will `be` 1 200 secondes, tandis que `localTime` à ce stade, `be` 900 secondes.

1. Restaurez la session utilisateur lorsque l’activité du lecteur reprend.

   TVSDK ne reprend pas la lecture entre les initialisations TVSDK, car il n’enregistre aucune information localement. Votre application doit implémenter cette logique.

   ```
   // retrieve the resumeTime from the persistent location 
   var resumeTime:Number:Number = ...;
   ```

1. Pour reprendre la vidéo à la même position :

   * Pour reprendre la lecture de la vidéo à partir de la position enregistrée lors d’une session précédente, utilisez `seekToLocal`.

     >[!TIP]
     >
     >Cette méthode est appelée uniquement avec les valeurs d’heure locale. Si la méthode est appelée avec les résultats de l’heure actuelle, un comportement incorrect se produit.

   * Pour rechercher l’heure actuelle, utilisez `seek`.

1. Lorsque votre demande reçoit la `onStatusChanged` changement d’état, recherchez l’heure locale enregistrée.
1. Fournissez les coupures publicitaires comme indiqué dans l’interface de stratégie publicitaire.
1. Implémentez un sélecteur de stratégie de publicité personnalisé en étendant le sélecteur de stratégie de publicité par défaut.
1. Fournir les coupures publicitaires qui doivent être présentées à l’utilisateur en implémentant `selectAdBreaksToPlay`.

   Lorsque le lecteur accède à l’état PRÉPARÉ , toutes les publicités sont déjà résolues, de sorte que la variable `AdPolicyInfo.adBreakTimelineItem` contient toutes les coupures publicitaires avant l’heure locale. Votre application peut décider de lire une coupure publicitaire preroll et de reprendre à l’heure locale spécifiée, de lire une coupure publicitaire mid-roll et de reprendre à l’heure locale spécifiée ou de ne pas lire d’coupures publicitaires.
