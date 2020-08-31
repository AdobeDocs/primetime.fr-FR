---
description: Dans le navigateur TVSDK, vous pouvez rechercher une position spécifique (heure) dans un flux. Un flux peut être une liste de lecture à fenêtre coulissante ou un contenu vidéo à la demande (VOD).
seo-description: Dans le navigateur TVSDK, vous pouvez rechercher une position spécifique (heure) dans un flux. Un flux peut être une liste de lecture à fenêtre coulissante ou un contenu vidéo à la demande (VOD).
seo-title: Gérer la recherche lors de l’utilisation de la barre de recherche
title: Gérer la recherche lors de l’utilisation de la barre de recherche
uuid: a7c74141-581f-40a3-9d28-ce56ba56773c
translation-type: tm+mt
source-git-commit: 1985694f99c548284aad6e6b4e070bece230bdf4
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# Gérer la recherche lors de l’utilisation de la barre de recherche{#handle-seek-when-using-the-seek-bar}

Dans le navigateur TVSDK, vous pouvez rechercher une position spécifique (heure) dans un flux. Un flux peut être une liste de lecture à fenêtre coulissante ou un contenu vidéo à la demande (VOD).

>[!IMPORTANT]
>
>La recherche dans un flux en direct n&#39;est autorisée que pour le magnétoscope numérique.

1. Attendez que le navigateur TVSDK soit dans un état valide pour la recherche.

   Les états valides sont PRÉPARÉS, TERMINÉS, PAUSED et PLAYING. Le fait d&#39;être dans un état valide garantit que la ressource multimédia a été chargée avec succès. Si le lecteur n’est pas dans un état de recherche valide, la tentative d’appel des méthodes suivantes renvoie une erreur `IllegalStateException`.

   Par exemple, vous pouvez attendre que le navigateur TVSDK se déclenche `AdobePSDK.MediaPlayerStatusChangeEvent` avec une valeur `event.status` de `AdobePSDK.MediaPlayerStatus.PREPARED`.

1. Transmettez la position de recherche demandée à la `MediaPlayer.seek` méthode en tant que paramètre en millisecondes.

   Cette opération déplace la tête de lecture à une position différente dans le flux.

   >[!TIP]
   >
   >Il se peut que la position de recherche demandée ne coïncide pas avec la position calculée réelle.

   ```js
   void seek(long position) throws IllegalStateException;
   ```

1. Attendez que le navigateur TVSDK déclenche le `AdobePSDK.PSDKEventType.SEEK_END` événement, qui renvoie la position ajustée dans l’attribut `actualPosition` du événement :

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.SEEK_END, onSeekComplete); 
   onSeekComplete = function (event) {
       // event.actualPosition
   }
   ```

   Ceci est important car la position réelle du début après la recherche peut être différente de celle demandée. Certaines des règles suivantes peuvent s’appliquer :

   * Le comportement de lecture est affecté si une recherche, ou tout autre repositionnement, se termine au milieu d’une coupure publicitaire ou saute des pauses publicitaires.
   * Vous ne pouvez effectuer des recherches que dans la durée recherchée de la ressource. Pour VOD, il s’agit de 0 jusqu’à la durée de l’actif.

1. Pour la barre de recherche créée dans l’exemple ci-dessus, écoutez pour `setPositionChangeListener()` savoir quand l’utilisateur fait défiler :

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

1. Configurez des rappels d’écouteur de événement pour les modifications apportées à l’activité de recherche de l’utilisateur.

       L’opération de recherche est asynchrone. Par conséquent, le navigateur TVSDK distribue ces événements liés à la recherche :
   
   * `AdobePSDK.PSDKEventType.SEEK_BEGIN` pour indiquer que la recherche est en cours.
   * `AdobePSDK.PSDKEventType.SEEK_END` pour indiquer que la recherche a réussi.
   * `AdobePSDK.PSDKEventType.SEEK_POSITION_ADJUSTED` pour indiquer que le lecteur multimédia a réajusté la position de recherche fournie par l’utilisateur.

