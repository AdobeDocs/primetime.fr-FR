---
description: Vous pouvez configurer un emplacement pour gérer les erreurs.
title: Configuration de la gestion des erreurs
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# Configuration de la gestion des erreurs {#set-up-error-handling}

Vous pouvez configurer un emplacement pour gérer les erreurs.

1. Mise en oeuvre d’une fonction de rappel d’événement pour `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK transmet des informations sur l’événement, telles qu’une `MediaPlayerStatusChangeEvent` .
1. Dans le rappel, lorsque l’état renvoyé est `MediaPlayerStatus.ERROR`, indiquez la logique pour gérer toutes les erreurs.
1. Une fois l’erreur traitée, réinitialisez la variable `MediaPlayer` ou charger une nouvelle ressource multimédia.

   Lorsque la variable `MediaPlayer` est dans l’état d’erreur, il reste dans cet état jusqu’à ce que vous le réinitialisiez à l’aide de la fonction `MediaPlayer.reset` .

<!--<a id="example_E74BB605ED08450295B8902F1E4BB8F5"></a>-->

Par exemple :

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
