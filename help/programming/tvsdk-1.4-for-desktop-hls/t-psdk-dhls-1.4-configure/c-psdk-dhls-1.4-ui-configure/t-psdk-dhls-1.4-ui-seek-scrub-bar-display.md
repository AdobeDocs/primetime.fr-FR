---
description: TVSDK prend en charge la recherche d'une position spécifique (temps) où le flux est une liste de lecture de fenêtre coulissante, à la fois dans la vidéo à la demande (VOD) et les flux en direct.
seo-description: TVSDK prend en charge la recherche d'une position spécifique (temps) où le flux est une liste de lecture de fenêtre coulissante, à la fois dans la vidéo à la demande (VOD) et les flux en direct.
seo-title: Affichage d’une barre de défilement de recherche avec la position de lecture actuelle
title: Affichage d’une barre de défilement de recherche avec la position de lecture actuelle
uuid: f940b305-4893-4531-9a79-53670f5fd23f
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Affichage d’une barre de défilement de recherche avec la position de lecture actuelle{#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK prend en charge la recherche d&#39;une position spécifique (temps) où le flux est une liste de lecture de fenêtre coulissante, à la fois dans la vidéo à la demande (VOD) et les flux en direct.

>[!IMPORTANT]
>
>La recherche dans un flux en direct n’est autorisée que pour le DVR.

1. Configurez les rappels pour la recherche.

       La recherche étant asynchrone, TVSDK distribue les  de recherche suivantes :
   
   * `SeekEvent.SEEK_BEGIN` - Cherche à démarrer.
   * `SeekEvent.SEEK_END` - Recherche réussie.
   * `SeekEvent.SEEK_POSITION_ADJUSTED` - réajusté la position de recherche fournie par l&#39;utilisateur.

1. Attendez que le lecteur soit dans un état valide pour la recherche.

   Les états valides sont PREPARRED, COMPLETED, PAUSED et PLAYING.

1. Prêtez attention au  approprié pour savoir quand l’utilisateur fait défiler l’écran.
1. Transmettez la position de recherche demandée (millisecondes) à la `MediaPlayer.seek` méthode.

   ```
   function seek(position:Number):void;
   ```

   Vous pouvez effectuer une recherche uniquement dans la durée recherchée de la ressource. Pour la vidéo à la demande, la durée est comprise entre 0 et la durée de la ressource.

   >[!TIP]
   >
   >Cela déplace la tête de lecture vers une nouvelle position dans le flux, mais la position finale calculée peut différer de la position de recherche spécifiée.

1. Attendez que TVSDK distribue le `SeekEvent.SEEK_END` .
1. Récupérez la position de lecture modifiée finale à l’aide de .currentPosition.

       C’est important car la position réelle du après la recherche peut être différente de la position demandée. Diverses règles peuvent s’appliquer, notamment :
   
   * Le comportement de lecture est affecté lorsqu’une recherche ou un autre repositionnement se termine au milieu d’une coupure publicitaire ou saute des pauses publicitaires.
   * Si vous effectuez une recherche près d’une limite de segment, la position de recherche est ajustée au début du segment.

1. Utilisez les informations de position lors de l’affichage d’une barre de défilement de recherche.
