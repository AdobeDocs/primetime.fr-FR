---
description: Vous pouvez utiliser TVSDK pour récupérer des informations sur la position du lecteur dans le média et les afficher dans la barre de recherche.
title: Afficher la durée, l’heure actuelle et l’heure restante de la vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Afficher la durée, l’heure actuelle et l’heure restante de la vidéo {#display-the-duration-current-time-and-remaining-time-of-the-video}

Vous pouvez utiliser TVSDK pour récupérer des informations sur la position du lecteur dans le média et les afficher dans la barre de recherche.

1. Attendez que le lecteur soit à au moins l’état PRÉPARÉ .
1. Récupérez l’heure actuelle du curseur de lecture à l’aide de la variable `MediaPlayer.getCurrentTime` .

   Cette opération renvoie la position actuelle du curseur de lecture sur la chronologie virtuelle en millisecondes. Le temps est calculé par rapport au flux résolu qui peut contenir plusieurs instances de contenu alternatif, comme plusieurs publicités ou coupures publicitaires répliquées dans le flux principal. Pour les flux en direct/linéaires, l’heure renvoyée se trouve toujours dans la plage de la fenêtre de lecture.

   ```java
   long getCurrentTime() throws MediaPlayerException;
   ```

1. Récupérez la plage de lecture de la diffusion et déterminez la durée.
   1. Utilisez la variable `MediaPlayer.getPlaybackRange` pour obtenir la plage temporelle de la chronologie virtuelle.

      ```java
      TimeRange getPlaybackRange() throws MediaPlayerException;
      ```

   1. Utilisez la variable `MediaPlayer.getPlaybackRange` pour obtenir la plage temporelle de la chronologie virtuelle.

      * Pour VOD, la plage commence toujours par zéro et la valeur de fin est égale à la somme de la durée du contenu principal et des durées du contenu supplémentaire dans le flux (publicités).
      * Pour une ressource linéaire/active, la plage représente la plage de la fenêtre de lecture. Cette plage change pendant la lecture.

        TVSDK appelle la fonction `ITEM_Updated` rappel pour indiquer que l’élément multimédia a été actualisé et que ses attributs, y compris la plage de lecture, ont été mis à jour.

1. Utilisation des méthodes disponibles sur `MediaPlayer` et sur le `SeekBar` dans le SDK Android pour configurer les paramètres de barre de recherche.

   Par exemple, voici une disposition possible qui contient la barre de recherche et deux `TextView` éléments .

   ```xml
   <LinearLayout 
    android:id="@+id/controlBarLayout" 
    android:layout_width="match_parent" 
    android:layout_height="wrap_content" 
    android:layout_alignParentBottom="true" 
    android:background="@android:color/black" 
    android:orientation="horizontal" > 
    <TextView 
       android:id="@+id/playerCurrentTimeText" 
       android:layout_width="wrap_content" 
       android:layout_height="wrap_content" 
       android:layout_margin="7dp" 
       android:text="00:00" 
       android:textColor="@android:color/white" /> 
    <SeekBar 
       android:id="@+id/playerSeekBar" 
       android:layout_width="wrap_content" 
       android:layout_height="wrap_content" 
       android:layout_weight="1" /> 
    <TextView 
       android:id="@+id/playerTotalTimeText" 
       android:layout_width="wrap_content" 
       android:layout_height="wrap_content" 
       android:layout_margin="7dp" 
       android:text="00:00" 
       android:textColor="@android:color/white" /> 
   </LinearLayout>
   ```

1. Utilisez un minuteur pour récupérer périodiquement l’heure actuelle et mettre à jour la barre de recherche, comme illustré dans la figure :

   <!--<a id="fig_689CEDDD02094C0C8E91C5195F8EAD3F"></a>-->

   ![](assets/seek-bar.jpg){width="477.000pt"}

   L’exemple suivant utilise la méthode `Clock.java` Classe d’assistance disponible dans `ReferencePlayer`, comme minuteur. Cette classe définit un écouteur d’événement et déclenche une `onTick` toutes les secondes ou une autre valeur de délai d’expiration que vous pouvez spécifier.

   ```java
   playbackClock = new Clock(PLAYBACK_CLOCK, CLOCK_TIMER); 
   playbackClockEventListener = new Clock.ClockEventListener() { 
       @Override 
       public void onTick(String name) { 
           // Timer event is received. Update the seek bar here. 
       } 
   }; 
   playbackClock.addClockEventListener(playbackClockEventListener);
   ```

   Sur chaque coche de l’horloge, cet exemple récupère la position actuelle du lecteur multimédia et met à jour la barre de recherche. Elle utilise les deux `TextView` pour marquer l’heure actuelle et la position de fin de la plage de lecture comme des valeurs numériques.

   ```java
   @Override 
   public void onTick(String name) { 
       if (mediaPlayer != null &&  
         mediaPlayer.getStatus() == MediaPlayerStatus.PLAYING) { 
           handler.post(new Runnable() { 
               @Override 
               public void run() { 
                   seekBar.setProgress((int) mediaPlayer.getCurrentTime()); 
                   currentTimeText.setText(timeStampToText(mediaPlayer.getCurrentTime())); 
                   totalTimeText.setText(timeStampToText(mediaPlayer.getPlaybackRange().getEnd())); 
               } 
           }); 
       } 
   } 
   ```
