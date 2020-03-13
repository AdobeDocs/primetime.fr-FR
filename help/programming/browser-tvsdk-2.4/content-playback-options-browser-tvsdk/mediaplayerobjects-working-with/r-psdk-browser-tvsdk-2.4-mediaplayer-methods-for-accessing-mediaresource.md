---
description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
seo-description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
seo-title: Attributs MediaPlayer pour accéder aux informations MediaResource
title: Attributs MediaPlayer pour accéder aux informations MediaResource
uuid: d26f39d6-0a6b-4072-b99a-8767a511a846
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Attributs MediaPlayer pour accéder aux informations MediaResource{#mediaplayer-attributes-to-access-mediaresource-information}

Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.

<table frame="all" colsep="1" rowsep="1" id="table_46225307CA5B4BB1869576E0B9141E38"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Objectif </th> 
   <th colname="2" class="entry"> Attribut </th> 
   <th colname="3" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> Flux en direct </td> 
   <td colname="2"> <span class="codeph"> live </span> </td> 
   <td colname="3"> True si le flux est en direct ; false s’il s’agit de VOD. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="2"> Sous-titres </td> 
   <td colname="2"> <span class="codeph"> hasClosedCaptions </span> </td> 
   <td colname="3"> True si des pistes de sous-titrage sont disponibles. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> closeCaptionsTracks </span> </td> 
   <td colname="3"> Fournit un  de pistes de sous-titrage codé disponibles. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectedClosedCaptionsTrack </span> </td> 
   <td colname="3"> Récupère la piste de sous-titrage codé qui a été sélectionnée avec <span class="codeph"> selectClosedCaptionsTrack </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="2"> Autre son </td> 
   <td colname="2"> <span class="codeph"> hasAlternateAudio </span> </td> 
   <td colname="3"> <p>True si le flux comporte des pistes audio de remplacement. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> audioTracks </span> </td> 
   <td colname="3"> Fournit un  de pistes audio alternatives disponibles. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectedAudioTrack </span> </td> 
   <td colname="3"> 
    <ph>
      Récupère la piste audio actuellement sélectionnée qui a été sélectionnée avec <span class="codeph"> selectAudioTrack </span>. 
    </ph> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="1"> Métadonnées minutées </td> 
   <td colname="2"> <span class="codeph"> hasTimedMetadata </span> </td> 
   <td colname="3"> True si le flux est associé à des métadonnées temporisées. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> timedMetadata </span> </td> 
   <td colname="3"> Fournit un des objets de métadonnées minutés associés au flux. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="1">  multiples (débit) </td> 
   <td colname="2" morerows="1"> <span class="codeph"> </span> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="3"> Fournit un  du de débit binaire associé à ce flux. <p>Remarque :  Vous pouvez récupérer le débit binaire pour chaque  de, ainsi que la hauteur et la largeur du  de. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Ressource média </td> 
   <td colname="2"> <span class="codeph"> ressource </span> </td> 
   <td colname="3"> Renvoie la ressource média associée à cet élément. </td> 
  </tr> 
 </tbody> 
</table>

