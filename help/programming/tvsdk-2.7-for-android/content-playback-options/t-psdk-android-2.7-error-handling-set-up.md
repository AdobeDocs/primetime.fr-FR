---
description: Vous pouvez configurer un emplacement pour gérer les erreurs.
seo-description: Vous pouvez configurer un emplacement pour gérer les erreurs.
seo-title: Configuration de la gestion des erreurs
title: Configuration de la gestion des erreurs
uuid: fde47fa5-5ca5-4be5-a7e7-3227c5e4c670
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# Configuration de la gestion des erreurs {#set-up-error-handling}

Vous pouvez configurer un emplacement pour gérer les erreurs.

1. Implémentez une fonction de rappel de  pour `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK transmet des informations , telles qu’un `MediaPlayerStatusChangeEvent` objet.
1. Dans le rappel, lorsque l’état renvoyé est `MediaPlayerStatus.ERROR`défini, fournissez une logique pour gérer toutes les erreurs.
1. Une fois l’erreur traitée, réinitialisez l’ `MediaPlayer` objet ou chargez une nouvelle ressource multimédia.

   Lorsque l’ `MediaPlayer` objet est dans l’état d’erreur, il reste dans cet état jusqu’à ce que vous le réinitialisiez à l’aide de la `MediaPlayer.reset` méthode.

<!--<a id="example_E74BB605ED08450295B8902F1E4BB8F5"></a>-->

Par exemple :

```java
mediaPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        if (event.getStatus() == MediaPlayerStatus.ERROR) { 
        // handle TVSDK error here 
        } 
    } 
});
```

