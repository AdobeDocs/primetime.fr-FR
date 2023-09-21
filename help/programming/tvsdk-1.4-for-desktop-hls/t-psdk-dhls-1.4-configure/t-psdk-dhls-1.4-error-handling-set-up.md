---
description: Configurez un seul emplacement pour gérer les erreurs.
title: Configuration de la gestion des erreurs
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---

# Configuration de la gestion des erreurs{#set-up-error-handling}

Configurez un seul emplacement pour gérer les erreurs.

1. Mise en oeuvre d’une fonction de rappel d’événement pour `MediaPlayerStatusChangeEvent.STATUS_CHANGED`.

   TVSDK transmet des informations sur l’événement, telles qu’une `MediaPlayerStatusChangeEvent` .
1. Dans le rappel, lorsque l’état du paramètre d’événement est `MediaPlayerStatus.ERROR`, indiquez la logique pour gérer toutes les erreurs.
1. Une fois l’erreur traitée, réinitialisez la variable `MediaPlayer` ou charger une nouvelle ressource multimédia.

   Lorsque la variable `MediaPlayer` est à l’état ERROR, il ne peut pas quitter cet état tant que vous n’avez pas réinitialisé la variable `MediaPlayer` (via l’objet `MediaPlayer.reset` ou charger une nouvelle ressource multimédia ( `MediaPlayer.replaceCurrentItem`).

<!--<a id="example_49FF225E92EA494AA06B2E5F26101F4C"></a>-->

Par exemple :

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
