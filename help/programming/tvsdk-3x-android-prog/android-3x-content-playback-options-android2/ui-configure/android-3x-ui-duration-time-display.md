---
description: Vous pouvez utiliser TVSDK pour récupérer des informations sur la position du lecteur dans le média et les afficher dans la barre de recherche.
seo-description: Vous pouvez utiliser TVSDK pour récupérer des informations sur la position du lecteur dans le média et les afficher dans la barre de recherche.
seo-title: Affiche la durée, l’heure actuelle et l’heure restante de la vidéo.
title: Affiche la durée, l’heure actuelle et l’heure restante de la vidéo.
uuid: 29bb6bc2-dab1-4f35-abcf-d3213605ee70
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Affiche la durée, l’heure actuelle et l’heure restante de la vidéo. {#display-the-duration-current-time-and-remaining-time-of-the-video}

Vous pouvez utiliser TVSDK pour récupérer des informations sur la position du lecteur dans le média et les afficher dans la barre de recherche.

1. Attendez que le lecteur soit au moins à l’état PRÉPARÉ.
1. Récupérez l’heure actuelle du curseur de lecture à l’aide de la `MediaPlayer.getCurrentTime` méthode.

   Cette opération renvoie la position actuelle du curseur de lecture sur le plan de montage chronologique virtuel en millisecondes. Le temps est calculé par rapport au flux résolu qui peut contenir plusieurs instances de contenu alternatif, telles que plusieurs publicités ou coupures publicitaires épissées dans le flux principal. Pour les flux en direct/linéaires, l’heure renvoyée se trouve toujours dans la plage de la fenêtre de lecture.

   ```java
   long getCurrentTime() throws MediaPlayerException;
   ```

1. Récupérez la plage de lecture du flux et déterminez sa durée.
   1. Utilisez la `MediaPlayer.getPlaybackRange` méthode pour obtenir la plage de temps de la chronologie virtuelle.

      ```java
      TimeRange getPlaybackRange() throws MediaPlayerException;
      ```

   1. Utilisez la `MediaPlayer.getPlaybackRange` méthode pour obtenir la plage de temps de la chronologie virtuelle.

      * Pour VOD, la plage commence toujours par zéro et la valeur finale est égale à la somme de la durée du contenu principal et de la durée du contenu supplémentaire dans le flux (publicités).
      * Pour un fichier linéaire/actif, la plage représente la plage de la fenêtre de lecture. Cette plage change pendant la lecture.

         TVSDK appelle le `ITEM_Updated` rappel pour indiquer que l’élément média a été actualisé et que ses attributs, y compris la plage de lecture, ont été mis à jour.

1. Utilisez les méthodes disponibles sur `MediaPlayer` et sur la `SeekBar` classe dans le SDK Android pour configurer les paramètres de barre de recherche.

   Par exemple, voici une disposition possible qui contient la barre de recherche et deux `TextView` éléments.

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

1. Utilisez un minuteur pour récupérer périodiquement l’heure actuelle et mettre à jour la barre de recherche, comme le montre la figure :

   <!--<a id="fig_689CEDDD02094C0C8E91C5195F8EAD3F"></a>-->

   ![](assets/seek-bar.jpg){width=&quot;477.000pt&quot;}

   L&#39;exemple suivant utilise la classe `Clock.java` helper, qui est disponible dans `ReferencePlayer`, comme minuteur. Cette classe définit un écouteur de événement et déclenche un `onTick` événement toutes les secondes ou une autre valeur de délai d&#39;expiration que vous pouvez spécifier.

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

   Sur chaque coche d&#39;horloge, cet exemple récupère la position actuelle du lecteur multimédia et met à jour la barre de recherche. Il utilise les deux `TextView` éléments pour marquer l’heure actuelle et la position de fin de la plage de lecture comme des valeurs numériques.

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
