---
description: Configurez un emplacement unique pour gérer les erreurs.
title: Configuration de la gestion des erreurs
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 2%

---


# Configurer la gestion des erreurs {#set-up-error-handling}

Configurez un emplacement unique pour gérer les erreurs.

1. Implémentez une fonction de rappel de événement pour `MediaPlayerStatusChangeEvent.STATUS_CHANGED`.

   TVSDK transmet des informations sur le événement, par exemple un objet `MediaPlayerStatusChangeEvent`.
1. Dans le rappel, lorsque l’état du paramètre de événement est `MediaPlayerStatus.ERROR`, indiquez la logique permettant de gérer toutes les erreurs.
1. Une fois l’erreur gérée, réinitialisez l’objet `MediaPlayer` ou chargez une nouvelle ressource multimédia.

   Lorsque l&#39;objet `MediaPlayer` est à l&#39;état ERROR, il ne peut pas quitter cet état tant que vous n&#39;avez pas réinitialisé l&#39;objet `MediaPlayer` (par la méthode `MediaPlayer.reset`) ou chargé une nouvelle ressource multimédia ( `MediaPlayer.replaceCurrentItem`).

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

