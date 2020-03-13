---
description: Dans le SDK du navigateur, vous pouvez rechercher une position spécifique (heure) dans un flux. Un flux peut être une liste de lecture à fenêtre coulissante ou un contenu vidéo à la demande (VOD).
seo-description: Dans le SDK du navigateur, vous pouvez rechercher une position spécifique (heure) dans un flux. Un flux peut être une liste de lecture à fenêtre coulissante ou un contenu vidéo à la demande (VOD).
seo-title: Gérer la recherche lors de l’utilisation de la barre de recherche
title: Gérer la recherche lors de l’utilisation de la barre de recherche
uuid: a7c74141-581f-40a3-9d28-ce56ba56773c
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Gérer la recherche lors de l’utilisation de la barre de recherche{#handle-seek-when-using-the-seek-bar}

Dans le SDK du navigateur, vous pouvez rechercher une position spécifique (heure) dans un flux. Un flux peut être une liste de lecture à fenêtre coulissante ou un contenu vidéo à la demande (VOD).

>[!IMPORTANT]
>
>La recherche dans un flux en direct n’est autorisée que pour le DVR.

1. Attendez que le navigateur TVSDK soit dans un état valide pour la recherche.

   Les états valides sont PREPARRED, COMPLETE, PAUSED et PLAYING. Le fait d’être dans un état valide garantit le chargement réussi de la ressource multimédia. Si le lecteur n’est pas dans un état de recherche valide, la tentative d’appel des méthodes suivantes renvoie une erreur `IllegalStateException`.

   Par exemple, vous pouvez attendre que le SDK du navigateur se déclenche `AdobePSDK.MediaPlayerStatusChangeEvent` avec une valeur `event.status` de `AdobePSDK.MediaPlayerStatus.PREPARED`.

1. Transmettez la position de recherche demandée à la `MediaPlayer.seek` méthode en tant que paramètre en millisecondes.

   Cette opération déplace la tête de lecture vers une position différente dans le flux.

   >[!TIP]
   >
   >La position de recherche demandée peut ne pas coïncider avec la position calculée réelle.

   ```js
   void seek(long position) throws IllegalStateException;
   ```

1. Attendez que le navigateur TVSDK déclenche la  du `AdobePSDK.PSDKEventType.SEEK_END` , qui renvoie la position ajustée dans l’attribut de  de `actualPosition` :

       &quot;js
     player.addEventListener(AdobePSDK.PSDKEventType.SEEK_END, onSeekComplete);
       onSeekComplete = fonction () {
     // .position
 réelle     }
     &quot;C&#39;est important car la position de l&#39;après la recherche peut être différente de la position demandée. 
    
     Certaines des règles suivantes peuvent s’appliquer :
   
   * Le comportement de lecture est affecté si une recherche, ou tout autre repositionnement, se termine au milieu d’une coupure publicitaire ou saute des pauses publicitaires.
   * Vous pouvez effectuer une recherche uniquement dans la durée recherchée de la ressource. Pour VOD, c’est-à-dire de 0 à la durée de l’actif.

1. Pour la barre de recherche créée dans l’exemple ci-dessus, écoutez `setPositionChangeListener()` pour savoir quand l’utilisateur fait défiler :

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

1. Configurez des rappels d’écouteurs  pour les modifications apportées au de recherche  de l’utilisateur.

       L’opération de recherche est asynchrone. Par conséquent, le navigateur TVSDK distribue ces  liés à la recherche :
   
   * `AdobePSDK.PSDKEventType.SEEK_BEGIN` pour indiquer que la recherche commence.
   * `AdobePSDK.PSDKEventType.SEEK_END` pour indiquer que la recherche a réussi.
   * `AdobePSDK.PSDKEventType.SEEK_POSITION_ADJUSTED` pour indiquer que le lecteur de médias a réajusté la position de recherche fournie par l’utilisateur.

