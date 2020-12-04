---
description: Vous pouvez enregistrer la position de lecture actuelle dans une vidéo et reprendre la lecture à la même position dans une session ultérieure.
seo-description: Vous pouvez enregistrer la position de lecture actuelle dans une vidéo et reprendre la lecture à la même position dans une session ultérieure.
seo-title: Enregistrer la position de la vidéo et reprendre ultérieurement
title: Enregistrer la position de la vidéo et reprendre ultérieurement
uuid: 322f780d-09ba-44b0-b2e5-46288bf58fda
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---


# Enregistrez la position de la vidéo et reprenez ultérieurement {#save-the-video-position-and-resume-later}

Vous pouvez enregistrer la position de lecture actuelle dans une vidéo et reprendre la lecture à la même position dans une session ultérieure.

Les publicités insérées dynamiquement diffèrent d’une session utilisateur à l’autre. Par conséquent, l’enregistrement de la position **avec** les publicités épissées fait référence à une position différente dans une session ultérieure. TVSDK fournit des méthodes pour récupérer la position de lecture tout en ignorant les publicités épissées.

1. Lorsque l’utilisateur ferme une vidéo, votre application récupère et enregistre la position dans la vidéo.

   >[!TIP]
   >
   >Les durées des publicités ne sont pas incluses.

   Les coupures publicitaires peuvent varier d’une session à l’autre en raison de modèles publicitaires, d’un plafonnement de fréquence, etc. L’heure actuelle de la vidéo dans une session peut être différente dans une session ultérieure. Lors de l’enregistrement d’une position dans la vidéo, l’application récupère l’heure locale, que vous pouvez enregistrer sur le périphérique ou dans une base de données sur le serveur.

   Par exemple, si l’utilisateur se trouve à la 20e minute de la vidéo et que cette position comprend cinq minutes de publicités, `getCurrentTime` renvoie 1 200 secondes, tandis que `getLocalTime` à cette position renvoie 900 secondes.

   >[!IMPORTANT]
   >
   >L’heure locale et l’heure actuelle sont identiques pour les flux en direct/linéaires. Dans ce cas, `convertToLocalTime` n&#39;a aucun effet. Pour VOD, l’heure locale reste inchangée pendant la lecture des publicités.

   ```java
   // Save the user session when player activity stops 
   @Override 
   public void onStop() { 
       super.onStop(); 
       ... 
       prefs = PreferenceManager.getDefaultSharedPreferences( 
                 getActivity().getApplicationContext() 
               ); 
       SharedPreferences.Editor editor = prefs.edit(); 
       // get the local time where stream stopped playing and  
       // save it in System preferences 
       editor.putLong(LAST_LOCAL_TIME, _mediaPlayer.getLocalTime());  
       editor.putString(LAST_MEDIA_RESOURCE, _contentInfo.toMediaResource().getUrl()); 
       editor.commit(); 
       ... 
   } 
   ```

1. Restaurez la session utilisateur lorsque l’activité du lecteur reprend.

   ```java
   @Override 
   public void onResume() { 
       super.onResume(); 
       ... 
       prefs = PreferenceManager.getDefaultSharedPreferences(getActivity().getApplicationContext()); 
       if (prefs.getString(LAST_MEDIA_RESOURCE, "nil").equals(_contentInfo.toMediaResource().getUrl())) { 
   
           _lastKnownLocalTime = prefs.getLong(LAST_LOCAL_TIME, 0);    // get the last local time saved  
                                                                       // in system preferences 
           if (_lastKnownLocalTime > 0) { 
               _shouldResumePlayback = true; 
           } 
       } 
       ... 
   } 
   ```

1. Pour reprendre la vidéo à la même position :

   * Pour reprendre la lecture de la vidéo à partir de la position enregistrée lors d&#39;une session précédente, utilisez `seekToLocalTime`.

      >[!TIP]
      >
      >Cette méthode est appelée uniquement avec des valeurs d’heure locales. Si la méthode est appelée avec les résultats de l’heure actuelle, un comportement incorrect se produit.

   * Pour rechercher l&#39;heure actuelle, utilisez `seek`.

1. Lorsque votre application reçoit le événement de modification d&#39;état `onStatusChanged`, recherchez l&#39;heure locale enregistrée.

   ```java
   private final MediaPlayer.PlaybackEventListener _playbackEventListener =  
     new MediaPlayer.PlaybackEventListener() { 
       @Override 
       public void onPrepared() { 
           ... 
           if (_shouldResumePlayback) { 
               if(_lastKnownLocalTime >= 0) { 
                   _mediaPlayer.seekToLocalTime(_lastKnownLocalTime); 
               } 
           } 
           ... 
       } 
        ... 
   } 
   ```

1. Fournissez les coupures publicitaires comme spécifié dans l’interface de stratégie publicitaire.
1. Implémentez un sélecteur de stratégies publicitaires personnalisé en étendant le sélecteur de stratégies publicitaires par défaut.
1. Fournissez les coupures publicitaires qui doivent être présentées à l’utilisateur en implémentant `selectAdBreaksToPlay`.

   Cette méthode comprend une coupure publicitaire preroll et des coupures publicitaires mid-roll avant la position horaire locale. Votre application peut décider de lire une coupure publicitaire preroll et de reprendre à l’heure locale spécifiée, de lire une coupure publicitaire mid-roll et de reprendre à l’heure locale spécifiée, ou de ne pas lire de coupures publicitaires.
