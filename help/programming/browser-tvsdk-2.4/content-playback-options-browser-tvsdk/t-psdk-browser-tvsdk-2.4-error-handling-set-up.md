---
description: Vous pouvez configurer un emplacement dans votre application pour gérer les erreurs en réponse à l’état ERROR.
title: Configuration de la gestion des erreurs
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Configuration de la gestion des erreurs{#set-up-error-handling}

Vous pouvez configurer un emplacement dans votre application pour gérer les erreurs en réponse à l’état ERROR.

1. Ajout d’un écouteur d’événement pour `AdobePSDK.MediaPlayerStatusChangeEvent`.

   Par exemple :

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, 
                           onStatusChange);
   ```

1. Dans votre écouteur d’événement, lorsque la variable `event.status` is `AdobePSDK.MediaPlayerStatus.ERROR`, indiquez la logique pour gérer toutes les erreurs.
1. Une fois l’erreur traitée, réinitialisez la variable `MediaPlayer` ou charger une nouvelle ressource multimédia.

       Lorsque l’objet MediaPlayer est à l’état ERROR, il ne peut pas quitter cet état tant que vous n’avez pas effectué l’une des tâches suivantes :
   
   * Réinitialisez l’objet MediaPlayer à l’aide de la fonction `MediaPlayer.reset` .
   * Chargement d’une nouvelle ressource multimédia à l’aide de la fonction `MediaPlayer.replaceCurrentResource` .

<!--<a id="example_342CA5A8CD7C45BD88233C5BDBB17220"></a>-->

Par exemple :

```js
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange); 
onStatusChange = function (event) { 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.ERROR: 
            //handle error 
            break; 
    } 
} 
```
