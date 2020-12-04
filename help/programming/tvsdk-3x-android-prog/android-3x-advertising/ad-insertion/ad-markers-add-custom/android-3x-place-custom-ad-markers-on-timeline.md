---
description: Cet exemple montre la méthode recommandée pour inclure des marqueurs publicitaires personnalisés dans le plan de montage chronologique de lecture.
seo-description: Cet exemple montre la méthode recommandée pour inclure des marqueurs publicitaires personnalisés dans le plan de montage chronologique de lecture.
seo-title: Placez des marqueurs publicitaires personnalisés sur le plan de montage chronologique.
title: Placez des marqueurs publicitaires personnalisés sur le plan de montage chronologique.
uuid: 47e31a97-e5da-46f3-bdcc-327c159c4355
translation-type: tm+mt
source-git-commit: 2a6ea34968ee7085931f99a24dfb23d097721b89
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# Placez des marqueurs publicitaires personnalisés sur la chronologie {#place-custom-ad-markers-on-the-timeline}

Cet exemple montre la méthode recommandée pour inclure des marqueurs publicitaires personnalisés dans le plan de montage chronologique de lecture.

1. Traduisez les informations de positionnement publicitaire out-of-band dans une liste/un tableau de classe `RepaceTimeRange`.
1. Créez une instance de la classe `CustomRangeMetadata` et utilisez sa méthode `setTimeRangeList` avec la liste/le tableau comme argument pour définir sa liste de plage de temps.
1. Utilisez sa méthode `setType` pour définir le type sur `MARK_RANGE`.
1. Utilisez la méthode `MediaPlayerItemConfig.setCustomRangeMetadata` avec l&#39;instance `CustomRangeMetadata` comme argument pour définir les métadonnées de plage personnalisée.
1. Utilisez la méthode `MediaPlayer.replaceCurrentResource` avec l&#39;instance `MediaPlayerItemConfig` comme argument pour définir la nouvelle ressource comme ressource active.
1. Attendez un événement `STATE_CHANGED` qui indique que le lecteur est à l’état `PREPARED`.
1. Début de la lecture vidéo en appelant `MediaPlayer.play`.

Voici le résultat de l’exécution des tâches dans cet exemple :

* Si un `ReplaceTimeRange` chevauche un autre élément du plan de montage chronologique de lecture, par exemple, la position de début d’un `ReplaceTimeRange` est antérieure à la position de fin déjà placée, TVSDK ajuste en silence le début du `ReplaceTimeRange` incriminé pour éviter le conflit.

   Ceci raccourcit le `ReplaceTimeRange` ajusté par rapport à celui spécifié initialement. Si l’ajustement conduit à une durée de zéro, TVSDK supprime en silence l’élément `ReplaceTimeRange` incriminé.

* TVSDK recherche des plages horaires adjacentes pour les coupures publicitaires personnalisées et les regroupe en sauts publicitaires distincts.

Les plages temporelles qui ne sont adjacentes à aucune autre plage temporelle sont traduites en coupures publicitaires contenant une seule publicité.

* Si l’application tente de charger une ressource multimédia dont la configuration contient `CustomRangeMetadata` qui ne peut être utilisée que dans les marqueurs publicitaires personnalisés contextuels, TVSDK renvoie une exception si la ressource sous-jacente n’est pas de type VOD.

* Lorsqu’il s’agit de marques publicitaires personnalisées, TVSDK désactive d’autres mécanismes de résolution de publicités (par exemple, la prise de décision publicitaire Adobe Primetime).

   Vous pouvez utiliser n’importe quel module de résolution de publicités TVSDK ou le mécanisme de balisage publicitaire personnalisé. Lorsque vous utilisez des marqueurs publicitaires personnalisés, le contenu de la publicité est considéré comme résolu et est placé sur le plan de montage chronologique.

Le fragment de code suivant place trois plages de temps sur le plan de montage chronologique en tant que marqueurs publicitaires personnalisés.

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
