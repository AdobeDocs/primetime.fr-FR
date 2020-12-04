---
description: Vous pouvez utiliser TVSDK pour récupérer des informations sur le média que vous pouvez afficher dans la barre de recherche.
seo-description: Vous pouvez utiliser TVSDK pour récupérer des informations sur le média que vous pouvez afficher dans la barre de recherche.
seo-title: Affiche la durée, l’heure actuelle et l’heure restante de la vidéo.
title: Affiche la durée, l’heure actuelle et l’heure restante de la vidéo.
uuid: afb43169-2d82-4137-ba38-27caef3d8c21
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# Affiche la durée, l’heure actuelle et l’heure restante de la vidéo{#display-the-duration-current-time-and-remaining-time-of-the-video}

Vous pouvez utiliser TVSDK pour récupérer des informations sur le média que vous pouvez afficher dans la barre de recherche.

1. Attendez que votre lecteur soit à l’état PRÉPARÉ.
1. Récupérez l’heure actuelle du curseur de lecture à l’aide de la méthode `MediaPlayer.getCurrentTime`.

   Cette opération renvoie la position actuelle du curseur de lecture sur le plan de montage chronologique virtuel en millisecondes. Le temps est calculé par rapport au flux résolu qui peut contenir plusieurs instances de contenu alternatif, telles que plusieurs publicités ou coupures publicitaires épissées dans le flux principal. Pour les flux en direct/linéaires, l’heure renvoyée se trouve toujours dans la plage de la fenêtre de lecture.

   ```java
   long getCurrentTime() throws IllegalStateException;
   ```

1. Récupérez la plage de lecture du flux et déterminez sa durée.
   1. Utilisez la méthode `mediaPlayer.getPlaybackRange` pour obtenir la plage de temps de la chronologie virtuelle.

      ```java
      TimeRange getPlaybackRange() throws IllegalStateException;
      ```

   1. Analyse de la période à l&#39;aide de `mediacore.utils.TimeRange`.
   1. Pour déterminer la durée, soustrayez le début de la fin de la plage.

      Cela inclut la durée du contenu supplémentaire qui est inséré dans le flux (publicités).

      Pour VOD, la plage commence toujours par zéro et la valeur finale est égale à la somme de la durée du contenu principal et de la durée du contenu supplémentaire inséré dans le flux (publicités).

      Pour un fichier linéaire/vivant, la plage représente la plage de la fenêtre de lecture et cette plage change pendant la lecture.

      TVSDK appelle votre rappel `onUpdated` pour indiquer que l’élément média a été actualisé et que ses attributs (y compris la plage de lecture) ont été mis à jour.

1. Utilisez les méthodes disponibles sur les classes `MediaPlayer` et `SeekBar` qui sont accessibles au public dans le SDK Android pour configurer les paramètres de barre de recherche.

   Par exemple, voici une disposition possible qui contient les éléments `SeekBar` et deux éléments `TextView`.

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

1. Utilisez un minuteur pour récupérer régulièrement l’heure actuelle et mettre à jour SeekBar.

   L&#39;exemple suivant utilise la classe d&#39;assistance `Clock.java` comme minuteur, disponible dans le lecteur de référence PrimetimeReference. Cette classe définit un écouteur de événement et déclenche un événement `onTick` toutes les secondes, ou une autre valeur de délai d&#39;expiration que vous pouvez spécifier.

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

   Sur chaque tic d&#39;horloge, cet exemple récupère la position actuelle du lecteur multimédia et met à jour la barre de recherche. Il utilise les deux éléments TextView pour marquer l’heure actuelle et la position de fin de la plage de lecture comme des valeurs numériques.

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

