---
description: Vous pouvez enregistrer la position de lecture actuelle dans une vidéo et reprendre la lecture à la même position dans une session ultérieure.
title: Enregistrer la position de la vidéo et reprendre ultérieurement
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Enregistrer la position de la vidéo et reprendre ultérieurement {#save-the-video-position-and-resume-later}

Vous pouvez enregistrer la position de lecture actuelle dans une vidéo et reprendre la lecture à la même position dans une session ultérieure.

Les publicités insérées dynamiquement diffèrent d’une session utilisateur à l’autre, ce qui permet d’enregistrer la position. **avec** les publicités épissées font référence à une position différente dans une session ultérieure. TVSDK fournit des méthodes pour récupérer la position de lecture tout en ignorant les publicités épissées.

1. Lorsque l’utilisateur quitte une vidéo, votre application récupère et enregistre la position dans la vidéo.

   >[!TIP]
   >
   >Les durées des publicités ne sont pas incluses.

   Les coupures publicitaires peuvent varier au cours de chaque session en raison des schémas publicitaires, de la limitation de fréquence, etc. L’heure actuelle de la vidéo dans une session peut être différente dans une session ultérieure. Lors de l’enregistrement d’une position dans la vidéo, l’application récupère l’heure locale, que vous pouvez enregistrer sur le périphérique ou dans une base de données sur le serveur.

   Par exemple, si l’utilisateur se trouve à la 20e minute de la vidéo et que cette position inclut cinq minutes de publicités, `getCurrentTime` renvoie 1 200 secondes, tandis que `getLocalTime` à cette position, renvoie 900 secondes.

   >[!IMPORTANT]
   >
   >L’heure locale et l’heure actuelle sont les mêmes pour les flux linéaire/en direct. Dans ce cas, `convertToLocalTime` n’a aucun effet. Pour VOD, l’heure locale reste inchangée pendant la lecture des publicités.

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

   * Pour reprendre la lecture de la vidéo à partir de la position enregistrée lors d’une session précédente, utilisez `seekToLocalTime`.

     >[!TIP]
     >
     >Cette méthode est appelée uniquement avec les valeurs d’heure locale. Si la méthode est appelée avec les résultats de l’heure actuelle, un comportement incorrect se produit.

   * Pour rechercher l’heure actuelle, utilisez `seek`.

1. Lorsque votre demande reçoit la `onStatusChanged` changement d’état, recherchez l’heure locale enregistrée.

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

1. Fournissez les coupures publicitaires comme indiqué dans l’interface de stratégie publicitaire.
1. Implémentez un sélecteur de stratégie de publicité personnalisé en étendant le sélecteur de stratégie de publicité par défaut.
1. Fournir les coupures publicitaires qui doivent être présentées à l’utilisateur en implémentant `selectAdBreaksToPlay`.

   Cette méthode comprend une coupure publicitaire preroll et des coupures publicitaires mid-roll avant le poste horaire local. Votre application peut décider de lire une coupure publicitaire preroll et de reprendre à l’heure locale spécifiée, de lire une coupure publicitaire mid-roll et de reprendre à l’heure locale spécifiée ou de ne pas lire d’coupures publicitaires.
