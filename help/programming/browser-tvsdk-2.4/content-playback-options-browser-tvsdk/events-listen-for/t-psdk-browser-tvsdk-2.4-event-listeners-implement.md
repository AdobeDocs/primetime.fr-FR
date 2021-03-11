---
description: Les gestionnaires de événements permettent au navigateur TVSDK de répondre aux événements.
title: Mise en oeuvre des écouteurs et des rappels de événement
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 1%

---


# Mettre en oeuvre des écouteurs et des rappels de événement{#implement-event-listeners-and-callbacks}

Les gestionnaires de événements permettent au navigateur TVSDK de répondre aux événements.

Lorsqu&#39;un événement se produit, le mécanisme de événement du navigateur TVSDK appelle votre gestionnaire de événements enregistré et transmet les informations du événement au gestionnaire.

Votre application doit mettre en oeuvre des écouteurs de événement pour les événements Browser TVSDK qui affectent votre application.

1. Déterminez quels événements votre application doit écouter.

   * **Événements** requis : Prêtez attention à tous les événements de lecture.

      >[!IMPORTANT]
      >
      >Le événement de lecture `STATUS_CHANGED` fournit l’état du lecteur, y compris les erreurs. L’un des états peut affecter l’étape suivante de votre lecteur.

   * **Autres événements** : Facultatif, selon votre application.

      Par exemple, si vous incorporez de la publicité dans votre lecture, écoutez tous les événements `AdBreakPlaybackEvent` et `AdPlaybackEvent`.

1. Mettez en oeuvre des écouteurs de événement pour chaque événement.

   Le navigateur TVSDK renvoie des valeurs de paramètre à vos rappels d’écouteur de événement. Ces valeurs fournissent des informations pertinentes sur le événement que vous pouvez utiliser dans vos écouteurs pour effectuer les actions appropriées.

   Par exemple :

   * Type d&#39;événement : `AdobePSDK.PSDKEventType.STATUS_CHANGED`
   * Propriété du événement : `MediaPlayerStatus.<event>` utilisé comme suit :

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

1. Enregistrez vos écouteurs de rappel avec l&#39;objet `MediaPlayer` en utilisant `MediaPlayer.addEventListener`.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                                    onStatusChange);
   ```
