---
description: Les gestionnaires de  de navigateur permettent au TVSDK du navigateur de répondre aux  de.
seo-description: Les gestionnaires de  de navigateur permettent au TVSDK du navigateur de répondre aux  de.
seo-title: 'Mise en oeuvre des écouteurs et des rappels de '
title: 'Mise en oeuvre des écouteurs et des rappels de '
uuid: 63f62c60-505e-4f83-bc0d-58895d85a75a
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Mise en oeuvre des écouteurs et des rappels de{#implement-event-listeners-and-callbacks}

Les gestionnaires de  de navigateur permettent au TVSDK du navigateur de répondre aux  de.

Lorsqu’un se produit, le mécanisme de  du navigateur TVSDK appelle votre gestionnaire de deréseau enregistré et transmet les informations de l’au gestionnaire.

Votre application doit mettre en oeuvre  écouteurs pour le Browser TVSDK qui  affecter votre application.

1. Déterminez pour quel  votre application doit écouter.

   * **** obligatoire : Écoute tous les  de lecture.

      >[!IMPORTANT]
      >
      >Le de lecture `STATUS_CHANGED` fournit l’état du lecteur, y compris les erreurs. N’importe quel état peut affecter l’étape suivante de votre lecteur.

   * **Autre**: Facultatif, selon votre application.

      Si, par exemple, vous incorporez de la publicité dans votre lecture, écoutez tous les `AdBreakPlaybackEvent` et les `AdPlaybackEvent` .

1. Mettez en oeuvre des écouteurs  pour chaque  de.

   Le navigateur TVSDK renvoie des valeurs de paramètre à vos rappels d’écouteur de . Ces valeurs fournissent des informations pertinentes sur l’que vous pouvez utiliser dans vos écouteurs pour effectuer les actions appropriées.

   Par exemple :

   *  : `AdobePSDK.PSDKEventType.STATUS_CHANGED`
   * Propriété  : `MediaPlayerStatus.<event>` utilisé comme suit :

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
