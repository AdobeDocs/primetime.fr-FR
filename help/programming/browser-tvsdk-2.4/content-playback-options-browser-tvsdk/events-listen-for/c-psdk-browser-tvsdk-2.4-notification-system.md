---
description: La partie notification de la bibliothèque Browser TVSDK vous permet de créer un système de journalisation et de débogage qui peut être utile à des fins de diagnostic et de validation.
title: Système de notification
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Système de notification {#notification-system}

La partie notification de la bibliothèque Browser TVSDK vous permet de créer un système de journalisation et de débogage qui peut être utile à des fins de diagnostic et de validation.

<!--<a id="section_EC5DBE8DDA434B70A01FA2F3EF4618BD"></a>-->

Le navigateur TVSDK dispose d’un *pas de jeton* de son API. La plupart des méthodes renvoient une `PSDKErrorCode` pour indiquer si la méthode a bien été exécutée. Pour obtenir une liste complète de tous les éléments possibles `PSDKErrorCode` , voir Références de l’API TVSDK du navigateur.

Les erreurs asynchrones sont notifiées par le biais d’événements spécifiques.

Diffusions TVSDK du navigateur `MediaPlayer` pour fournir des informations sur l’activité du lecteur. Vous devez mettre en oeuvre des écouteurs d’événements pour capturer ces événements et y répondre.

>[!TIP]
>
>Les événements et informations clés sont consignés dans la console du navigateur web.

## Écoute des notifications {#section_06B96633433D497E842FB7ADD5F2C7DA}

Vous pouvez écouter les notifications et ajouter vos propres notifications à l’historique des notifications. Le coeur du système de notification Browser TVSDK est le suivant : `Notification` qui représente une notification autonome.

Pour configurer votre application afin d’écouter les notifications :

1. Prêtez attention aux modifications de l’état de MediaPlayer à l’aide de l’instance MediaPlayer.

   ```js
   player.addEventListener( 
         AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. Mettez en oeuvre le rappel .

   Le rappel reçoit une instance de la fonction `AdobePSDK.MediaPlayerStatusChangeEvent`et que le TVSDK du navigateur transmet cet objet d’événement au rappel qui contient le nouvel état du lecteur.
1. Votre application peut écouter d’autres événements distribués par le Browser TVSDK à l’aide de la fonction `MediaPlayer` instance.
