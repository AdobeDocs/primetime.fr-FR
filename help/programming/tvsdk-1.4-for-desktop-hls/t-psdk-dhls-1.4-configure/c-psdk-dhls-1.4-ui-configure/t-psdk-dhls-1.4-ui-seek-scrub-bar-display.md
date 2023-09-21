---
description: TVSDK prend en charge la recherche vers une position spécifique (heure) où la diffusion est une liste de lecture de fenêtre glissante, à la fois dans la vidéo à la demande (VOD) et dans les diffusions en direct.
title: Afficher une barre de défilement de recherche avec la position de lecture actuelle
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Afficher une barre de défilement de recherche avec la position de lecture actuelle{#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK prend en charge la recherche vers une position spécifique (heure) où la diffusion est une liste de lecture de fenêtre glissante, à la fois dans la vidéo à la demande (VOD) et dans les diffusions en direct.

>[!IMPORTANT]
>
>La recherche dans une diffusion en direct n’est autorisée que pour les enregistrements DVR.

1. Configurez les rappels pour la recherche.

       La recherche étant asynchrone, TVSDK distribue les événements liés à la recherche suivants :
   
   * `SeekEvent.SEEK_BEGIN` - Recherche en cours.
   * `SeekEvent.SEEK_END` - Recherche réussie.
   * `SeekEvent.SEEK_POSITION_ADJUSTED` : correction de la position de recherche fournie par l’utilisateur.

1. Attendez que le lecteur soit dans un état valide pour la recherche.

   Les états valides sont PRÉPARÉS, TERMINÉS, EN PAUSE et EN LECTURE.

1. Prêtez attention à l’événement approprié pour savoir quand l’utilisateur effectue un défilement.
1. Transmettez la position de recherche demandée (en millisecondes) à la variable `MediaPlayer.seek` .

   ```
   function seek(position:Number):void;
   ```

   Vous ne pouvez effectuer des recherches que dans la durée de recherche de la ressource. Pour une vidéo à la demande, la durée est comprise entre 0 et la durée de la ressource.

   >[!TIP]
   >
   >Cela déplace la tête de lecture vers une nouvelle position dans le flux, mais la position finale calculée peut différer de la position de recherche spécifiée.

1. Attendez que TVSDK distribue la variable `SeekEvent.SEEK_END` .
1. Récupérez la position de lecture finale ajustée à l’aide de event.realPosition.

       Ceci est important, car la position de départ réelle après la recherche peut être différente de celle requise. Diverses règles peuvent s’appliquer, notamment :
   
   * Le comportement de lecture est affecté si une recherche ou un autre repositionnement se termine au milieu d’une coupure publicitaire ou si elle ignore les coupures publicitaires.
   * Si vous effectuez une recherche près d’une limite de segment, la position de la recherche est ajustée au début du segment.

1. Utilisez les informations de position lors de l’affichage d’une barre de défilement de recherche.
