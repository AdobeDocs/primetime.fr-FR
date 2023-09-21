---
description: Cet exemple illustre la méthode recommandée pour inclure des marqueurs publicitaires personnalisés dans la chronologie de lecture.
title: Placement de marqueurs publicitaires personnalisés sur la chronologie
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Placement de marqueurs publicitaires personnalisés sur la chronologie {#place-custom-ad-markers-on-the-timeline}

Cet exemple illustre la méthode recommandée pour inclure des marqueurs publicitaires personnalisés dans la chronologie de lecture.

1. Traduisez les informations de positionnement des publicités hors-bande dans une liste ou un tableau de `RepaceTimeRange` classe .
1. Création d’une instance de `CustomRangeMetadata` et utilisez ses `setTimeRangeList` avec la liste/le tableau comme argument pour définir sa liste de périodes.
1. Utilisez `setType` pour définir le type sur `MARK_RANGE`.
1. Utilisez la variable `MediaPlayerItemConfig.setCustomRangeMetadata` avec la méthode `CustomRangeMetadata` comme argument pour définir les métadonnées de plage personnalisées.
1. Utilisez la variable `MediaPlayer.replaceCurrentResource` avec la méthode `MediaPlayerItemConfig` comme argument pour définir la nouvelle ressource sur la ressource active.
1. Attendez un événement `STATE_CHANGED` , qui indique que le lecteur se trouve dans la variable `PREPARED` état.
1. Commencez la lecture vidéo en appelant `MediaPlayer.play`.

Voici le résultat des tâches effectuées dans cet exemple :

* Si une `ReplaceTimeRange` chevauche une autre sur la chronologie de lecture, par exemple, la position de début d’une `ReplaceTimeRange` est antérieur à une position de fin déjà placée, TVSDK ajuste silencieusement le début de l’offense. `ReplaceTimeRange` pour éviter le conflit.

  Cela modifie le `ReplaceTimeRange` plus court que spécifié initialement. Si l’ajustement conduit à une durée de zéro, TVSDK supprime silencieusement l’offense `ReplaceTimeRange`.

* TVSDK recherche des plages horaires adjacentes pour les coupures publicitaires personnalisées et les regroupe dans des coupures publicitaires distinctes.

Les plages temporelles qui ne sont adjacentes à aucune autre plage temporelle sont traduites en coupures publicitaires contenant une seule publicité.

* Si l’application tente de charger une ressource multimédia dont la configuration contient `CustomRangeMetadata` pouvant être utilisé uniquement dans les marqueurs d’annonce personnalisés contextuels, TVSDK renvoie une exception si la ressource sous-jacente n’est pas de type VOD.

* Lorsque vous gérez des marqueurs publicitaires personnalisés, TVSDK désactive d’autres mécanismes de résolution des publicités (par exemple, Adobe Primetime et la prise de décision).

  Vous pouvez utiliser n’importe quel module de résolveur de publicités TVSDK ou le mécanisme de marqueurs de publicités personnalisés. Lorsque vous utilisez des marqueurs de publicité personnalisés, le contenu de la publicité est considéré comme résolu et placé dans la chronologie.

Le fragment de code suivant place trois plages de temps sur la chronologie en tant que marqueurs d’annonce personnalisés.

```java
// Assume that the 3 time ranges are obtained through external means 
// Use them to populate the ReplaceTimeRange instance 
List<ReplaceTimeRange> timeRanges = new ArrayList<ReplaceTimeRange>(); 
timeRanges.add(new ReplaceTimeRange(0,10000, 0)); 
timeRanges.add(new ReplaceTimeRange(15000,20000, 0)); 
timeRanges.add(new ReplaceTimeRange(25000,30000, 0)); 
 
CustomRangeMetadata customRangeMetadata = new CustomRangeMetadata(); 
customRangeMetadata.setTimeRangeList(timeRanges); 
customRangeMetadata.setType(CustomRangeMetadata.CustomRangeType.MARK_RANGE); 
 
//Create a MediaResource instance 
MediaResource mediaResource = MediaResource.createFromUrl( 
        "www.example.com/video/test_video.m3u8", timeRanges.toMedatada(null)); 
 
// Create a MediaPlayerItemConfig instance 
MediaPlayerItemConfig config =  
  new MediaPlayerItemConfig(getActivity().getApplicationContext()); 
 
// Set customRangeMetadata 
config.setCustomRangeMetadata(customRangeMetadata); 
 
// Prepare the content for playback by calling replaceCurrentResource 
// NOTE: mediaPlayer is an instance of a properly configured MediaPlayer  
mediaPlayer.replaceCurrentResource(mediaResource, config); 
 
// wait for TVSDK to reach the PREPARED state 
mediaPlayer.addEventListener(MediaPlayerEvent.STATE_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
 
    if( event.getStatus() == MediaPlayerStatus.PREPARED ) { 
        // TVSDK is in the PREPARED state, so start the playback  
        mediaPlayer.play(); 
    } 
    ... 
}
```
