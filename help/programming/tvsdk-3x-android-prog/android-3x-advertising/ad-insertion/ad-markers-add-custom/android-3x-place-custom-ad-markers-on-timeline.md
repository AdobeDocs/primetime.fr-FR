---
description: Cet exemple montre la méthode recommandée pour inclure des marqueurs publicitaires personnalisés dans le plan de montage chronologique de la lecture.
seo-description: Cet exemple montre la méthode recommandée pour inclure des marqueurs publicitaires personnalisés dans le plan de montage chronologique de la lecture.
seo-title: Placez des marqueurs publicitaires personnalisés sur le plan de montage chronologique.
title: Placez des marqueurs publicitaires personnalisés sur le plan de montage chronologique.
uuid: 47e31a97-e5da-46f3-bdcc-327c159c4355
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Placez des marqueurs publicitaires personnalisés sur le plan de montage chronologique. {#place-custom-ad-markers-on-the-timeline}

Cet exemple montre la méthode recommandée pour inclure des marqueurs publicitaires personnalisés dans le plan de montage chronologique de la lecture.

1. Traduisez les informations de positionnement publicitaire hors bande dans un /tableau de `RepaceTimeRange` classe.
1. Créez une instance de `CustomRangeMetadata` classe et utilisez sa `setTimeRangeList` méthode avec le /tableau comme argument pour définir son de plage de temps.
1. Utilisez sa `setType` méthode pour définir le type `MARK_RANGE`.
1. Utilisez la `MediaPlayerItemConfig.setCustomRangeMetadata` méthode avec l’ `CustomRangeMetadata` instance comme argument pour définir les métadonnées de plage personnalisée.
1. Utilisez la `MediaPlayer.replaceCurrentResource` méthode avec l’ `MediaPlayerItemConfig` instance comme argument pour définir la nouvelle ressource comme ressource active.
1. Attendez un `STATE_CHANGED` , qui indique que le lecteur est à l’ `PREPARED` état.
1. de la lecture vidéo en appelant `MediaPlayer.play`.

Voici le résultat de l’achèvement du  du dans cet exemple :

* Si une `ReplaceTimeRange` séquence se superpose à une autre sur le plan de montage chronologique de la lecture, par exemple, si la position  d’une `ReplaceTimeRange` est antérieure à la position de fin déjà placée, TVSDK ajuste en silence le de l’élément offensant `ReplaceTimeRange` pour éviter le conflit.

   Le réglage est donc `ReplaceTimeRange` plus court que celui indiqué initialement. Si l’ajustement conduit à une durée de zéro, TVSDK supprime en silence l’offense `ReplaceTimeRange`.

* TVSDK recherche des plages horaires adjacentes pour les coupures publicitaires personnalisées et les regroupe dans des pauses publicitaires distinctes.

Les plages temporelles qui ne sont adjacentes à aucune autre plage temporelle sont converties en pauses publicitaires contenant une seule publicité.

* Si l’application tente de charger une ressource multimédia dont la configuration contient `CustomRangeMetadata` qui ne peut être utilisée que dans les marqueurs publicitaires personnalisés contextuels, TVSDK renvoie une exception si la ressource sous-jacente n’est pas de type VOD.

* Lorsque vous traitez de marques publicitaires personnalisées, TVSDK désactive d’autres mécanismes de résolution des publicités (par exemple, la prise de décision publicitaire Adobe Primetime).

   Vous pouvez utiliser n’importe quel module de résolution de publicités TVSDK ou le mécanisme de marqueurs publicitaires personnalisés. Lorsque vous utilisez des marqueurs publicitaires personnalisés, le contenu de la publicité est considéré comme résolu et est placé dans le plan de montage chronologique.

Le fragment de code suivant place trois plages de temps sur le plan de montage chronologique en tant que marqueurs publicitaires personnalisés.
>```java>
>// Assume that the 3 time ranges are obtained through external means 
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
```>

