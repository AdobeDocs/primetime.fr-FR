---
description: Vous pouvez configurer un emplacement dans votre application pour effectuer la gestion des erreurs en réponse à l’état ERROR.
title: Configuration de la gestion des erreurs
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 3%

---


# Configurer la gestion des erreurs {#set-up-error-handling}

Vous pouvez configurer un emplacement dans votre application pour effectuer la gestion des erreurs en réponse à l’état ERROR.

1. Ajoutez un écouteur de événement pour `AdobePSDK.MediaPlayerStatusChangeEvent`.

   Par exemple :

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, 
                           onStatusChange);
   ```

1. Dans votre écouteur de événement, lorsque `event.status` est `AdobePSDK.MediaPlayerStatus.ERROR`, indiquez la logique permettant de gérer toutes les erreurs.
1. Une fois l’erreur gérée, réinitialisez l’objet `MediaPlayer` ou chargez une nouvelle ressource multimédia.

       Lorsque l’objet MediaPlayer est à l’état ERROR, il ne peut pas quitter cet état tant que vous n’avez pas effectué l’une des tâches suivantes :
   
   * Réinitialisez l’objet MediaPlayer à l’aide de la méthode `MediaPlayer.reset`.
   * Chargez une nouvelle ressource multimédia à l&#39;aide de la méthode `MediaPlayer.replaceCurrentResource`.

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

