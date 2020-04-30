---
description: Configurez un emplacement unique pour gérer les erreurs.
seo-description: Configurez un emplacement unique pour gérer les erreurs.
seo-title: Configuration de la gestion des erreurs
title: Configuration de la gestion des erreurs
uuid: a3182fce-85ac-4dad-bdb3-f9bfbdb2c62d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Configuration de la gestion des erreurs{#set-up-error-handling}

Configurez un emplacement unique pour gérer les erreurs.

1. Implémentez une fonction de rappel de événement pour `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK transmet des informations sur le événement, par exemple un `MediaPlayerStatusChangeEvent` objet.
1. Dans le rappel, lorsque l’état renvoyé est `MediaPlayerState.ERROR`défini, fournissez une logique pour gérer toutes les erreurs.
1. Une fois l’erreur gérée, réinitialisez l’ `MediaPlayer` objet ou chargez une nouvelle ressource multimédia.

   Lorsque l’ `MediaPlayer` objet est à l’état d’erreur, il reste dans cet état jusqu’à ce que vous le réinitialisiez à l’aide de la `MediaPlayer.reset` méthode.

<!--<a id="example_49FF225E92EA494AA06B2E5F26101F4C"></a>-->

Par exemple :

```java
mediaPlayer.addEventListener( 
  MediaPlayerEvent.STATUS_CHANGED, new StatusChangedEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        if (event.getStatus() == MediaPlayerStatus.ERROR) { 
            // handle TVSDK error here 
        } 
    } 
});
```

