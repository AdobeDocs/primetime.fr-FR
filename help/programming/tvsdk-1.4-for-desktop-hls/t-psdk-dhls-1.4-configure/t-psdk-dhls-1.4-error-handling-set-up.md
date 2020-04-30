---
description: Configurez un emplacement unique pour gérer les erreurs.
seo-description: Configurez un emplacement unique pour gérer les erreurs.
seo-title: Configuration de la gestion des erreurs
title: Configuration de la gestion des erreurs
uuid: ff56180d-aa74-4b7c-a24c-e536d874c2e6
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Configuration de la gestion des erreurs{#set-up-error-handling}

Configurez un emplacement unique pour gérer les erreurs.

1. Implémentez une fonction de rappel de événement pour `MediaPlayerStatusChangeEvent.STATUS_CHANGED`.

   TVSDK transmet des informations sur le événement, par exemple un `MediaPlayerStatusChangeEvent` objet.
1. Dans le rappel, lorsque l’état du paramètre de événement est `MediaPlayerStatus.ERROR`défini, fournissez une logique pour gérer toutes les erreurs.
1. Une fois l’erreur gérée, réinitialisez l’ `MediaPlayer` objet ou chargez une nouvelle ressource multimédia.

   Lorsque l&#39; `MediaPlayer` objet est à l&#39;état ERROR, il ne peut pas quitter cet état tant que vous n&#39;avez pas réinitialisé l&#39; `MediaPlayer` objet (par la `MediaPlayer.reset` méthode) ou chargé une nouvelle ressource média ( `MediaPlayer.replaceCurrentItem`).

<!--<a id="example_49FF225E92EA494AA06B2E5F26101F4C"></a>-->

Par exemple :

```
mediaPlayer.addEventListener(MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
                             onStatusChanged); 
 
private void onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
    if (event.status == MediaPlayerStatus.ERROR) { 
        var error:MediaError = event.error; 
        // handle TVSDK error here 
    } 
} 
```

