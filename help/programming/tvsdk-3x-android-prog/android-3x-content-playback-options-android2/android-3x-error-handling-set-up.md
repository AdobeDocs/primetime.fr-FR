---
description: Vous pouvez configurer un emplacement pour gérer les erreurs.
seo-description: Vous pouvez configurer un emplacement pour gérer les erreurs.
seo-title: Configuration de la gestion des erreurs
title: Configuration de la gestion des erreurs
uuid: 7c122830-6259-4e95-882e-fb1700454e6e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 1%

---


# Configurer la gestion des erreurs {#set-up-error-handling}

Vous pouvez configurer un emplacement pour gérer les erreurs.

1. Implémentez une fonction de rappel de événement pour `MediaPlayerEvent.STATUS_CHANGED`.

   TVSDK transmet des informations sur le événement, par exemple un objet `MediaPlayerStatusChangeEvent`.
1. Dans le rappel, lorsque l’état renvoyé est `MediaPlayerStatus.ERROR`, fournissez la logique permettant de gérer toutes les erreurs.
1. Une fois l’erreur gérée, réinitialisez l’objet `MediaPlayer` ou chargez une nouvelle ressource multimédia.

   Lorsque l&#39;objet `MediaPlayer` est dans l&#39;état d&#39;erreur, il reste dans cet état jusqu&#39;à ce que vous le réinitialisiez à l&#39;aide de la méthode `MediaPlayer.reset`.

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
