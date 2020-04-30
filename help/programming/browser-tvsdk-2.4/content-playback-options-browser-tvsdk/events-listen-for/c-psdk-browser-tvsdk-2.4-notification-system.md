---
description: La partie notification de la bibliothèque du navigateur TVSDK vous permet de créer un système de journalisation et de débogage qui peut être utile à des fins de diagnostic et de validation.
seo-description: La partie notification de la bibliothèque du navigateur TVSDK vous permet de créer un système de journalisation et de débogage qui peut être utile à des fins de diagnostic et de validation.
seo-title: Système de notification
title: Système de notification
uuid: 69c4ff1d-3167-413b-ab49-942a5ddc34d7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Système de notification {#notification-system}

La partie notification de la bibliothèque du navigateur TVSDK vous permet de créer un système de journalisation et de débogage qui peut être utile à des fins de diagnostic et de validation.

<!--<a id="section_EC5DBE8DDA434B70A01FA2F3EF4618BD"></a>-->

Le navigateur TVSDK a une stratégie de *non-renvoi* pour son API. La plupart des méthodes renvoient une `PSDKErrorCode` valeur pour indiquer si la méthode a bien été exécutée. Pour obtenir une liste complète de toutes les `PSDKErrorCode` valeurs possibles, consultez les références d’API du navigateur TVSDK.

Les erreurs asynchrones sont signalées par le biais de événements spécifiques.

Le navigateur TVSDK distribue `MediaPlayer` des événements pour fournir des informations sur l’activité du lecteur. Vous devez implémenter des écouteurs de événement pour capturer ces événements et y répondre.

>[!TIP]
>
>Les événements clés et les informations sont consignés dans la console du navigateur Web.

## Écoute des notifications {#section_06B96633433D497E842FB7ADD5F2C7DA}

Vous pouvez écouter les notifications et ajouter vos propres notifications à l’historique des notifications. Le coeur du système de notification du navigateur TVSDK est la `Notification` classe, qui représente une notification autonome.

Pour configurer votre application afin qu’elle écoute les notifications :

1. Prêtez attention aux modifications d’état de MediaPlayer en utilisant l’instance MediaPlayer.

   ```js
   player.addEventListener( 
         AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. Implémentez le rappel.

   Le rappel reçoit une instance de la `AdobePSDK.MediaPlayerStatusChangeEvent`, et le navigateur TVSDK transmet cet objet de événement au rappel qui contient le nouvel état du lecteur.
1. Votre application peut écouter d’autres événements qui sont distribués par le navigateur TVSDK à l’aide de l’ `MediaPlayer` instance.

