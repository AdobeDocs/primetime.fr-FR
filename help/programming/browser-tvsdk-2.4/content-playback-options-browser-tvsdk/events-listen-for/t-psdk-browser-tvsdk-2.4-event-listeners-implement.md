---
description: Les gestionnaires de Événements permettent au navigateur TVSDK de répondre aux événements.
seo-description: Les gestionnaires de Événements permettent au navigateur TVSDK de répondre aux événements.
seo-title: Mise en oeuvre des écouteurs et des rappels de événement
title: Mise en oeuvre des écouteurs et des rappels de événement
uuid: 63f62c60-505e-4f83-bc0d-58895d85a75a
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Mise en oeuvre des écouteurs et des rappels de événement{#implement-event-listeners-and-callbacks}

Les gestionnaires de Événements permettent au navigateur TVSDK de répondre aux événements.

Lorsqu&#39;un événement se produit, le mécanisme de événement du navigateur TVSDK appelle votre gestionnaire de événements enregistré et transmet les informations du événement au gestionnaire.

Votre application doit mettre en oeuvre des écouteurs de événement pour les événements Browser TVSDK qui affectent votre application.

1. Déterminez quels événements votre application doit écouter.

   * **événements** requis : Prêtez attention à tous les événements de lecture.

      >[!IMPORTANT]
      >
      >Le événement de lecture `STATUS_CHANGED` fournit l’état du lecteur, y compris les erreurs. L’un des états peut affecter l’étape suivante de votre lecteur.

   * **Autres événements**: Facultatif, selon votre application.

      Par exemple, si vous incorporez de la publicité dans votre lecture, écoutez tous les `AdBreakPlaybackEvent` `AdPlaybackEvent` événements et tous les autres.

1. Mettez en oeuvre des écouteurs de événement pour chaque événement.

   Le navigateur TVSDK renvoie des valeurs de paramètre à vos rappels d’écouteur de événement. Ces valeurs fournissent des informations pertinentes sur le événement que vous pouvez utiliser dans vos écouteurs pour effectuer les actions appropriées.

   Par exemple :

   * Type d&#39;événement : `AdobePSDK.PSDKEventType.STATUS_CHANGED`
   * Propriété du Événement : `MediaPlayerStatus.<event>` utilisé comme suit :

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

1. Enregistrez vos écouteurs de rappel avec l’ `MediaPlayer` objet à l’aide de `MediaPlayer.addEventListener`.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                                    onStatusChange);
   ```
