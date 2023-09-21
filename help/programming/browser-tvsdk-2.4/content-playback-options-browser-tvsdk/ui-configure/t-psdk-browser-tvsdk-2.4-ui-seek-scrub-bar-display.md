---
description: Dans Browser TVSDK, vous pouvez rechercher une position (heure) spécifique dans un flux. Un flux peut être une liste de lecture à fenêtre glissante ou un contenu vidéo à la demande (VOD).
title: Gérer la recherche lors de l’utilisation de la barre de recherche
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Gérer la recherche lors de l’utilisation de la barre de recherche{#handle-seek-when-using-the-seek-bar}

Dans Browser TVSDK, vous pouvez rechercher une position (heure) spécifique dans un flux. Un flux peut être une liste de lecture à fenêtre glissante ou un contenu vidéo à la demande (VOD).

>[!IMPORTANT]
>
>La recherche dans une diffusion en direct n’est autorisée que pour les enregistrements DVR.

1. Attendez que le SDK du navigateur soit dans un état valide pour la recherche.

   Les états valides sont PRÉPARÉS, TERMINÉS, EN PAUSE et EN LECTURE. Être dans un état valide garantit que la ressource multimédia a bien été chargée. Si le lecteur ne se trouve pas dans un état de recherche valide, la tentative d’appel des méthodes suivantes renvoie une `IllegalStateException`.

   Par exemple, vous pouvez attendre que le SDK du navigateur se déclenche.  `AdobePSDK.MediaPlayerStatusChangeEvent`  avec un `event.status` de `AdobePSDK.MediaPlayerStatus.PREPARED`.

1. Transmettez la position de la recherche demandée à la fonction `MediaPlayer.seek` comme paramètre en millisecondes.

   Cela déplace la tête de lecture vers une position différente dans le flux.

   >[!TIP]
   >
   >La position de recherche demandée peut ne pas correspondre à la position calculée réelle.

   ```js
   void seek(long position) throws IllegalStateException;
   ```

1. Attendez que le navigateur TVSDK déclenche la variable  `AdobePSDK.PSDKEventType.SEEK_END`  , qui renvoie la position ajustée dans la variable `actualPosition` attribute:

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.SEEK_END, onSeekComplete); 
   onSeekComplete = function (event) {
       // event.actualPosition
   }
   ```

   Ceci est important, car la position de départ réelle après la recherche peut être différente de la position demandée. Certaines des règles suivantes peuvent s’appliquer :

   * Le comportement de lecture est affecté si une recherche, ou un autre repositionnement, se termine au milieu d’une coupure publicitaire ou ignore les coupures publicitaires.
   * Vous ne pouvez effectuer des recherches que dans la durée de recherche de la ressource. Pour VOD, cela va de 0 à la durée de la ressource.

1. Pour la barre de recherche qui a été créée dans l’exemple ci-dessus, écoutez `setPositionChangeListener()` pour voir quand l’utilisateur effectue un défilement :

   ```js
   seekBar.setPositionChangeListener(function (pos) { 
                   var range = player.seekableRange; 
                   if (range) { 
                       var duration = range.duration; 
                       var time = duration * pos; // seek bar range is [0,1] 
                       player.seek(time); 
   
                       console.log("seek to " + time + " / " + duration); 
                   } 
   
               }); 
   ```

1. Configurez les rappels des écouteurs d’événements pour les modifications apportées à l’activité de recherche de l’utilisateur.

       L’opération de recherche est asynchrone. Par conséquent, le navigateur TVSDK distribue ces événements liés à la recherche :
   
   * `AdobePSDK.PSDKEventType.SEEK_BEGIN` pour indiquer que la recherche démarre.
   * `AdobePSDK.PSDKEventType.SEEK_END` pour indiquer que la recherche a réussi.
   * `AdobePSDK.PSDKEventType.SEEK_POSITION_ADJUSTED` pour indiquer que le lecteur multimédia a réajusté la position de recherche fournie par l’utilisateur.
