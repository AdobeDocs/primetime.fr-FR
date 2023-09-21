---
description: Les gestionnaires d’événements permettent au TVSDK du navigateur de répondre aux événements.
title: Mise en oeuvre des écouteurs d’événement et des rappels
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Mise en oeuvre des écouteurs d’événement et des rappels{#implement-event-listeners-and-callbacks}

Les gestionnaires d’événements permettent au TVSDK du navigateur de répondre aux événements.

Lorsqu’un événement se produit, le mécanisme d’événement du navigateur TVSDK appelle votre gestionnaire d’événements enregistré et transmet les informations d’événement au gestionnaire.

Votre application doit mettre en oeuvre des écouteurs d’événements pour les événements Browser TVSDK qui affectent votre application.

1. Déterminez les événements que votre application doit écouter.

   * **Événements requis**: écoute tous les événements de lecture.

     >[!IMPORTANT]
     >
     >Événement de lecture `STATUS_CHANGED` fournit l’état du lecteur, y compris les erreurs. L’un des états peut affecter l’étape suivante de votre lecteur.

   * **Autres événements**: facultatif, selon votre application.

     Par exemple, si vous incorporez de la publicité dans votre lecture, écoutez tous les `AdBreakPlaybackEvent` et `AdPlaybackEvent` événements .

1. Mettez en oeuvre des écouteurs d’événement pour chaque événement.

   Le navigateur TVSDK renvoie des valeurs de paramètre à vos rappels d’écouteurs d’événements. Ces valeurs fournissent des informations pertinentes sur l’événement que vous pouvez utiliser dans vos écouteurs pour effectuer les actions appropriées.

   Par exemple :

   * Type d’événement : `AdobePSDK.PSDKEventType.STATUS_CHANGED`
   * Propriété d’événement : `MediaPlayerStatus.<event>` utilisé comme suit :

```js
player.addEventListener( 
            AdobePSDK.PSDKEventType.STATUS_CHANGED,  
            onStatusChange); 
 
onStatusChange = function (event) { 
 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.IDLE: 
            console.log("Player Status: IDLE"); 
            break;
```

1. Enregistrez vos écouteurs de rappel avec l’événement `MediaPlayer` en utilisant `MediaPlayer.addEventListener`.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                                    onStatusChange);
   ```
