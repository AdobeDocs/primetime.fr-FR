---
description: TVSDK prend en charge la recherche à une position spécifique (temps) où le flux est une playlist de fenêtre coulissante, à la fois dans la vidéo à la demande (VOD) et les flux en direct.
title: Affichage d’une barre de défilement de recherche avec la position de lecture actuelle
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---


# Afficher une barre de défilement de recherche avec la position de lecture actuelle{#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK prend en charge la recherche à une position spécifique (temps) où le flux est une playlist de fenêtre coulissante, à la fois dans la vidéo à la demande (VOD) et les flux en direct.

>[!IMPORTANT]
>
>La recherche dans un flux en direct n&#39;est autorisée que pour le magnétoscope numérique.

1. Configurez les rappels pour la recherche.

       La recherche étant asynchrone, TVSDK distribue les événements suivants liés à la recherche :
   
   * `SeekEvent.SEEK_BEGIN` - Cherche à démarrer.
   * `SeekEvent.SEEK_END` - Recherche de succès.
   * `SeekEvent.SEEK_POSITION_ADJUSTED` - correction de la position de recherche fournie par l&#39;utilisateur.

1. Attendez que le lecteur ait un état valide pour la recherche.

   Les états valides sont PRÉPARÉS, TERMINÉS, PAUSED et PLAYING.

1. Prêtez attention au événement approprié pour savoir quand l’utilisateur effectue un balayage.
1. Transmettez la position de recherche demandée (millisecondes) à la méthode `MediaPlayer.seek`.

   ```
   function seek(position:Number):void;
   ```

   Vous ne pouvez effectuer des recherches que dans la durée recherchée de la ressource. Pour la vidéo à la demande, la durée est comprise entre 0 et la durée de la ressource.

   >[!TIP]
   >
   >Cela déplace la tête de lecture à une nouvelle position dans le flux, mais la position finale calculée peut différer de la position de recherche spécifiée.

1. Attendez que TVSDK distribue le événement `SeekEvent.SEEK_END`.
1. Récupérez la position de lecture modifiée finale à l’aide de événement.currentPosition.

       Ceci est important car la position réelle du début après la recherche peut être différente de la position demandée. Diverses règles peuvent s&#39;appliquer, notamment :
   
   * Le comportement de lecture est affecté si une recherche ou un autre repositionnement se termine au milieu d’une coupure publicitaire ou saute des pauses publicitaires.
   * Si vous effectuez une recherche près d’une limite de segment, la position de recherche est ajustée au début du segment.

1. Utilisez les informations de position lors de l&#39;affichage d&#39;une barre de défilement de recherche.
