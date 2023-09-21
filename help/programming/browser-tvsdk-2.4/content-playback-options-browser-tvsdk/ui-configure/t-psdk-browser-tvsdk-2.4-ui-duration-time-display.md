---
description: Vous pouvez utiliser le navigateur TVSDK pour récupérer les informations sur le média que vous pouvez afficher dans la barre de recherche.
title: Afficher la durée, l’heure actuelle et l’heure restante de la vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---

# Afficher la durée, l’heure actuelle et l’heure restante de la vidéo{#display-the-duration-current-time-and-remaining-time-of-the-video}

Vous pouvez utiliser le navigateur TVSDK pour récupérer les informations sur le média que vous pouvez afficher dans la barre de recherche.

1. Attendez que votre lecteur soit à au moins l’état PRÉPARÉ .
1. Récupérez l’heure actuelle du curseur de lecture à l’aide de la variable `MediaPlayer.currentTime` attribut.

   Cet attribut renvoie la position actuelle du curseur de lecture sur la chronologie virtuelle en millisecondes. Le temps est calculé par rapport au flux résolu qui peut contenir plusieurs instances de contenu alternatif, comme plusieurs publicités ou coupures publicitaires répliquées dans le flux principal. Pour les flux en direct/linéaires, l’heure renvoyée se trouve toujours dans la plage de la fenêtre de lecture.

   ```js
   MediaPlayer.currentTime
   ```

1. Récupérez la plage de lecture de la diffusion et déterminez la durée.
   1. Utilisez la variable  `mediaPlayer.playbackRange` pour obtenir la plage temporelle de la chronologie virtuelle.

   1. Pour déterminer la durée, soustrayez le début de la fin de la période.

      Cela inclut la durée du contenu supplémentaire inséré dans le flux (publicités).

      Pour VOD, la plage commence toujours par zéro et la valeur de fin est égale à la somme de la durée du contenu principal et des durées du contenu supplémentaire inséré dans le flux (publicités).

      Pour une ressource linéaire/vivante, la plage représente la plage de la fenêtre de lecture, et cette plage change pendant la lecture.

1. Utilisez les méthodes disponibles sur les éléments MediaPlayer et Browser TVSDK pour configurer les paramètres de la barre de recherche.

   Par exemple, voici une disposition possible pour afficher la barre de recherche en HTML.

   ```
   <div class="seekbar" id="seekbar"> 
        <div> 
           <span class="backer" id="backer"></span> 
           <span class="buffer" id="buffer" ></span> 
           <div class="playhead" id="playhead"></div> 
                     <span class="progress" id="progress" ></span> 
           </div> 
         </div> 
     </div> 
   ```

   Voici le css correspondant :

   ```
   #seekbar { 
         position: relative; 
         width: 100%; 
         height: 16px; 
         cursor: pointer; 
         background: transparent; 
   } 
   
   #seekbar div { 
         position: relative; 
         height: 100%; 
         margin-left: 8px; 
         margin-right: 8px; 
   } 
   
   #seekbar span { 
         position: absolute; 
         height: 60%; 
         top: 20%; 
   
         display: block; 
   
         -webkit-border-radius: 16px; 
         -moz-border-radius: 16px; 
         border-radius: 16px; 
   } 
   
   #seekbar.playhead { 
        z-index: 1011; 
        height: 14px; 
        width: 14px; 
        border: 1px outset #c9cbce; 
        position: absolute; 
        left: -8px; /* adjust center of playhead over start of range */ 
        display: block; 
        padding: 0; 
        margin: 0; 
   
        background: #c9cbce; /* Old browsers */ 
        background: -moz-radial-gradient(circle, #4591ce 0%, #3080c2 40%, #c9cbce 45%, #dedee1 100%); /* FF3.6+ */ 
        background: -webkit-radial-gradient(circle, #4591ce 0%, #3080c2 40%, #c9cbce 45%, #dedee1 100%); /* Chrome10+,Safari5.1+ */ 
        background: -o-radial-gradient(circle, #4591ce 0%, #3080c2 40%, #c9cbce 45%, #dedee1 100%); /* Opera 11.10+ */ 
        background: -ms-radial-gradient(circle, #4591ce 0%, #3080c2 40%, #c9cbce 45%, #dedee1 100%); /* IE10+ */ 
        background: radial-gradient(circle, #4591ce 0%, #3080c2 40%, #c9cbce 45%, #dedee1 100%); /* W3C */ 
        filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#c9cbce', endColorstr='#dedee1',GradientType=0 ); /* IE6-9 */ 
   
        -webkit-border-radius: 16px; 
        -moz-border-radius: 16px; 
        border-radius: 16px; 
   } 
   
   #seekbar.backer { 
           z-index: 1004; 
           width: 100%; 
   
           background: #414142; /* Old browsers */ 
           background: -moz-linear-gradient(top,  #414142 0%, #343232 100%); /* FF3.6+ */ 
           background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,#414142), color-stop(100%,#343232)); /* Chrome,Safari4+ */ 
           background: -webkit-linear-gradient(top,  #414142 0%,#343232 100%); /* Chrome10+,Safari5.1+ */ 
           background: -o-linear-gradient(top,  #414142 0%,#343232 100%); /* Opera 11.10+ */ 
           background: -ms-linear-gradient(top,  #414142 0%,#343232 100%); /* IE10+ */ 
           background: linear-gradient(to bottom,  #414142 0%,#343232 100%); /* W3C */ 
           filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#414142', endColorstr='#343232',GradientType=0 ); /* IE6-9 */ 
   
   } 
   
   #seekbar .buffer { 
          z-index: 1005; 
          position: absolute; 
   
          background: #4b4b4c; /* Old browsers */ 
          background: -moz-linear-gradient(top,  #4b4b4c 0%, #818184 100%); /* FF3.6+ */ 
          background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,#4b4b4c), color-stop(100%,#818184)); /* Chrome,Safari4+ */ 
          background: -webkit-linear-gradient(top,  #4b4b4c 0%,#818184 100%); /* Chrome10+,Safari5.1+ */ 
          background: -o-linear-gradient(top,  #4b4b4c 0%,#818184 100%); /* Opera 11.10+ */ 
          background: -ms-linear-gradient(top,  #4b4b4c 0%,#818184 100%); /* IE10+ */ 
          background: linear-gradient(to bottom,  #4b4b4c 0%,#818184 100%); /* W3C */ 
          filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#4b4b4c', endColorstr='#818184',GradientType=0 ); /* IE6-9 */ 
   } 
   
   #seekbar .progress { 
           z-index: 1010; 
           position: absolute; 
   
           background: #4591ce; /* Old browsers */ 
           background: -moz-linear-gradient(top,  #4591ce 0%, #3080c2 100%); /* FF3.6+ */ 
           background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,#4591ce), color-stop(100%,#3080c2)); /* Chrome,Safari4+ */ 
           background: -webkit-linear-gradient(top,  #4591ce 0%,#3080c2 100%); /* Chrome10+,Safari5.1+ */ 
           background: -o-linear-gradient(top,  #4591ce 0%,#3080c2 100%); /* Opera 11.10+ */ 
           background: -ms-linear-gradient(top,  #4591ce 0%,#3080c2 100%); /* IE10+ */ 
           background: linear-gradient(to bottom,  #4591ce 0%,#3080c2 100%); /* W3C */ 
           filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#4591ce', endColorstr='#3080c2',GradientType=0 ); /* IE6-9 */ 
   } 
   ```

1. Listen for `AdobePSDK.TimeChangeEvent` et mettez à jour la barre de recherche en conséquence.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.TIME_CHANGED, onTimeChange); 
   
   /** 
        * Called when the player's time changes. 
        * Update UI to show current time, seekbar playhead position and buffer level. 
        */ 
        function onTimeChange(event) 
        { 
          if (!seekBar.isSeeking) { 
          var time = event.time; 
          var range = player.playbackRange; 
          seekBar.updatePlayhead(time, range); 
          updateDisplayTime(time, range); 
   
           var bufferedRange = player.bufferedRange; 
           seekBar.updateBufferLevel(bufferedRange.end, range); 
         } 
   
       } 
   ```

   Cet exemple crée un objet seekbar pour mettre à jour la barre de recherche :

   ```js
   /** 
       * Seekbar object which handles the display of the player progress,  
       * playhead, and buffer level. 
       */ 
       seekBar = (function () { 
   
       var playheadHalfSize = 8, // must be half width of playhead defined in CSS 
           containerElm = null, 
           playheadElm = null, 
           backerElm = null, 
           bufferElm = null, 
           progressElm = null, 
           currentPos = 0, // [0,1] relative to range 
           currentBuffer = 0,// [0,1] relative to range 
           listener = null, 
           isSeeking = false, 
   
            setPositionChangeListener = function (funct) { 
               listener = funct; 
            }, 
   
            getSeekBarBounds = function () { 
              return backerElm.getBoundingClientRect(); 
            }, 
   
            onPositionChange = function (event) { 
                var pos = event.pageX || event.clientX; 
                var bounds = getSeekBarBounds(); 
                // normalize position to seek bounds 
                pos -= bounds.left; 
                var percent = pos / (bounds.right - bounds.left); 
   
                // check bounds 
                 if (percent > 1) percent = 1; 
                 else if (percent < 0) percent = 0; 
   
                 currentPos = percent; 
                 setPosition(percent); 
              }, 
   
                 updatePlayhead = function (time, range) { 
                 if (!isSeeking) { 
                 var pos = convertTimeToRelativePosition(time, range); 
                 setPosition(pos); 
              } 
            }, 
   
               setPosition = function (percent) { 
               // adjust to keep playhead graphic inside container on right side 
               var bounds = getSeekBarBounds(); 
               var pos = percent * (bounds.right - bounds.left); 
   
               progressElm.style.width = (pos).toString() + "px"; 
               playheadElm.style.left = (pos-playheadHalfSize).toString() + "px"; 
   
               currentPos = percent; 
               return percent; 
   
               }, 
   
                updateBufferLevel = function (level, range) { 
                if (!isSeeking) { 
                    var position = convertTimeToRelativePosition(level, range); 
                    setBufferLevel(position); 
                   } 
               }, 
   
                 setBufferLevel = function (percent) { 
                    currentBuffer = percent; 
                    var bounds = getSeekBarBounds(); 
                    var pos = percent * (bounds.right - bounds.left); 
   
                           bufferElm.style.width = pos.toString() + "px"; 
                       }, 
   
                       resetSeekBar = function () { 
                          setPosition(currentPos); 
                          setBufferLevel(currentBuffer); 
                       }, 
   
                       convertTimeToRelativePosition = function (time, range) { 
                          // convert time to a percentage of the duration 
                          var position = (time - range.begin) / range.duration; 
                          if (position > 1) position = 1; 
                          else if (position < 0) position = 0; 
                          return position; 
                       }, 
   
                       unattachEvents = function (e) { 
                         this.removeEventListener('mousemove', onPositionChange); 
                         this.removeEventListener('mouseout', unattachEvents); 
                         this.removeEventListener('mouseup', unattachEvents); 
   
                           this.addEventListener('mouseover', attachEvents); 
                           isSeeking = false; 
                       }, 
   
                       attachEvents = function (e) { 
                          this.addEventListener('mousemove', onPositionChange); 
                          this.addEventListener('mouseout', unattachEvents); 
                          this.addEventListener('mouseup', unattachEvents); 
                          isSeeking = true; 
                          return false; 
                       }; 
   
               return  { 
                   init : function () { 
                     containerElm = document.getElementById("seekbar"); 
                     backerElm = document.getElementById("backer"); 
                     playheadElm = document.getElementById("playhead"); 
                     bufferElm = document.getElementById("buffer"); 
                     progressElm = document.getElementById("progress"); 
   
                     // client seek via scrubbing 
                     containerElm.addEventListener('mousedown', attachEvents); 
   
                     // client seek via single click or 'mouseup' after scrubbing 
                     containerElm.addEventListener('click', function (e) { 
                        if (listener !== null && !player.areControlsDisabledInAd()) { 
                           onPositionChange(e); 
                           // callback to notify of desired seek position 
                           listener.call(this, currentPos); 
                           } 
                       }); 
   
                       // end client seek via scrubbing 
                       document.addEventListener('mouseup', function (e) { 
                           containerElm.removeEventListener('mouseover', attachEvents); 
                       }); 
                   }, 
   
                  /** 
                  * Is the playhead currently being scrubbed. 
                  */ 
                  isSeeking : isSeeking, 
   
                  /** 
                  * Change the position of the playhead. 
                  * @param time - time in seconds to position playhead 
                  * @param range - current playback range 
                  */ 
                  updatePlayhead : updatePlayhead, 
   
                  /** 
                  * Change the position of the buffer range. 
                  * @param time - time in seconds to position head of buffer 
                  * @param range - current playback range 
                  */ 
                  updateBufferLevel : updateBufferLevel, 
   
                  /** 
                  * Set listener which is called when the playhead position changes 
                  * by the user event. Listener is not called when playhead position 
                  * changes via updatePlayhead function. 
                  * @param listener - callback function, passed single position argument 
                  * representing the playhead position in the range [0,1]. 
                  */ 
                  setPositionChangeListener : setPositionChangeListener, 
   
                  /** 
                  * Readjust position levels if seekbar is resized. 
                  * Should be called every time the video window changes size. 
                  */ 
                  readjustSeekBar : resetSeekBar 
               }; 
   
           })(); 
   ```
