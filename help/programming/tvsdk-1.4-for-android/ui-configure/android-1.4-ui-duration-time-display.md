---
description: Vous pouvez utiliser TVSDK pour récupérer des informations sur le média que vous pouvez afficher dans la barre de recherche.
title: Afficher la durée, l’heure actuelle et l’heure restante de la vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Afficher la durée, l’heure actuelle et l’heure restante de la vidéo{#display-the-duration-current-time-and-remaining-time-of-the-video}

Vous pouvez utiliser TVSDK pour récupérer des informations sur le média que vous pouvez afficher dans la barre de recherche.

1. Attendez que votre lecteur soit à l’état PRÉPARÉ.
1. Récupérez l’heure actuelle du curseur de lecture à l’aide de la variable `MediaPlayer.getCurrentTime` .

   Cette opération renvoie la position actuelle du curseur de lecture sur la chronologie virtuelle en millisecondes. Le temps est calculé par rapport au flux résolu qui peut contenir plusieurs instances de contenu alternatif, comme plusieurs publicités ou coupures publicitaires répliquées dans le flux principal. Pour les flux en direct/linéaires, l’heure renvoyée se trouve toujours dans la plage de la fenêtre de lecture.

   ```java
   long getCurrentTime() throws IllegalStateException;
   ```

1. Récupérez la plage de lecture de la diffusion et déterminez la durée.
   1. Utilisez la variable `mediaPlayer.getPlaybackRange` pour obtenir la plage temporelle de la chronologie virtuelle.

      ```java
      TimeRange getPlaybackRange() throws IllegalStateException;
      ```

   1. Parcourez la période à l’aide de `mediacore.utils.TimeRange`.
   1. Pour déterminer la durée, soustrayez le début de la fin de la période.

      Cela inclut la durée du contenu supplémentaire inséré dans le flux (publicités).

      Pour VOD, la plage commence toujours par zéro et la valeur de fin est égale à la somme de la durée du contenu principal et des durées du contenu supplémentaire inséré dans le flux (publicités).

      Pour une ressource linéaire/vivante, la plage représente la plage de la fenêtre de lecture, et cette plage change pendant la lecture.

      TVSDK appelle votre `onUpdated` rappel pour indiquer que l’élément multimédia a été actualisé et que ses attributs (y compris la plage de lecture) ont été mis à jour.

1. Utilisez les méthodes disponibles dans la variable `MediaPlayer` et la variable `SeekBar` qui est disponible publiquement dans le SDK Android pour configurer les paramètres de barre de recherche.

   Par exemple, voici une disposition possible qui contient le `SeekBar` et deux `TextView` éléments .

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

1. Utilisez un minuteur pour récupérer régulièrement l’heure actuelle et mettre à jour la barre de recherche.

   L’exemple suivant utilise la méthode `Clock.java` classe d’assistance comme minuteur, disponible dans le lecteur de référence PrimetimeReference. Cette classe définit un écouteur d’événement et déclenche une `onTick` toutes les secondes ou une autre valeur de délai d’expiration que vous pouvez spécifier.

   ```java
   playbackClock = new Clock(PLAYBACK_CLOCK, CLOCK_TIMER); 
   playbackClockEventListener = new Clock.ClockEventListener() { 
   @Override 
   public void onTick(String name) { 
       // Timer event is received. Update the SeekBar here. 
   } 
   }; 
   playbackClock.addClockEventListener(playbackClockEventListener);
   ```

   Sur chaque coche d’horloge, cet exemple récupère la position actuelle du lecteur multimédia et met à jour la barre de recherche. Elle utilise les deux éléments TextView pour marquer l’heure actuelle et la position de fin de la plage de lecture comme valeurs numériques.

   ```java
   @Override 
   public void onTick(String name) { 
   if (mediaPlayer != null && mediaPlayer.getStatus() == PlayerState.PLAYING) { 
       handler.post(new Runnable() { 
           @Override 
           public void run() { 
               seekBar.setProgress((int)  
                    mediaPlayer.getCurrentTime()); 
               currentTimeText.setText(timeStampToText( 
                  mediaPlayer.getCurrentTime())); 
               totalTimeText.setText(timeStampToText( 
                   mediaPlayer.getPlaybackRange().getEnd())); 
           } 
       }); 
   } 
   }
   ```
