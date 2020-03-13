---
description: Vous pouvez configurer un emplacement dans votre application pour effectuer la gestion des erreurs en réponse à l’état ERROR.
seo-description: Vous pouvez configurer un emplacement dans votre application pour effectuer la gestion des erreurs en réponse à l’état ERROR.
seo-title: Configuration de la gestion des erreurs
title: Configuration de la gestion des erreurs
uuid: 9e650ea7-86cb-4489-a3fd-80cd2ccef41f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Configuration de la gestion des erreurs{#set-up-error-handling}

Vous pouvez configurer un emplacement dans votre application pour effectuer la gestion des erreurs en réponse à l’état ERROR.

1. Ajouter un  d’écoute de pour `AdobePSDK.MediaPlayerStatusChangeEvent`.

   Par exemple :

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, 
                           onStatusChange);
   ```

1. Dans votre écouteur de , lorsque la `event.status` valeur est `AdobePSDK.MediaPlayerStatus.ERROR`, indiquez la logique permettant de gérer toutes les erreurs.
1. Une fois l’erreur traitée, réinitialisez l’ `MediaPlayer` objet ou chargez une nouvelle ressource multimédia.

       Lorsque l’objet MediaPlayer est à l’état ERROR, il ne peut pas quitter cet état tant que vous n’avez pas terminé l’un des  suivants :
   
   * Réinitialisez l’objet MediaPlayer à l’aide de la `MediaPlayer.reset` méthode.
   * Chargez une nouvelle ressource multimédia à l’aide de la `MediaPlayer.replaceCurrentResource` méthode.

<!--<a id="example_342CA5A8CD7C45BD88233C5BDBB17220"></a>-->

Par exemple :

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

