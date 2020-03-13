---
description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
seo-description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
seo-title: Méthodes MediaPlayer pour accéder aux informations MediaResource
title: Méthodes MediaPlayer pour accéder aux informations MediaResource
uuid: 5d83491c-6577-46fe-98af-83f0fde7a7d0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Méthodes MediaPlayer pour accéder aux informations MediaResource{#mediaplayer-methods-for-accessing-mediaresource-information}

Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.

<table frame="all" colsep="1" rowsep="1" id="table_77B55D506FE24326A03D97AA087231FF"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="2" class="entry"> Méthode </th> 
   <th colname="3" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Balises publicitaires</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;String&gt; getAdTags() </span> </td> 
   <td colname="3"> <p>Fournit le des balises publicitaires utilisées pour le processus d’emplacement des publicités. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Flux en direct</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen isLive(); </span> </td> 
   <td colname="3"> <p>True si le flux est en direct ; false s’il s’agit de VOD. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>DRM protégé</b> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen isProtected(); </span> </td> 
   <td colname="3"> <p>True si le flux est protégé par DRM. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;DRMMetadataInfo&gt; getDRMMetadataInfos(); </span> </td> 
   <td colname="3"> <p>tous les objets de métadonnées DRM découverts dans le manifeste. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Sous-titres</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen hasClosedCaptions(); </span> </td> 
   <td colname="3"> <p>True si des pistes de sous-titrage sont disponibles. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;ClosedCaptionsTrack&gt; getClosedCationsTracks(); </span> </td> 
   <td colname="3"> <p>Fournit un  de pistes de sous-titrage codé disponibles. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); </span> </td> 
   <td colname="3"> <p>Récupère la piste de sous-titrage codée actuelle sélectionnée avec <span class="codeph"> SelectClosedCaptionsTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack ( ClosedCaptionsTrack closeCaptionsTrack) </span> </td> 
   <td colname="3"> <p>Définit une piste de sous-titrage codé comme la piste de sous-titrage codé actuelle. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Autres pistes audio</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen hasAlternateAudio(); </span> </td> 
   <td colname="3"> <p>True si le flux comporte des pistes audio de remplacement. </p> <p>Conseil :  La piste audio principale (par défaut) fait également partie du de piste audio alternatif. </p> <p>TVSDK pour Android considère la piste audio principale comme l’un des éléments du de piste audio alternatif. Pour cette raison, le seul cas où <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> renvoie false est le cas lorsque le flux n’a pas du tout d’audio. Si le contenu ne comporte qu’une seule piste audio, cette méthode renvoie true et <span class="codeph"> MediaPlayerItem.getAudioTracks </span> renvoie un avec un seul élément (la piste audio par défaut). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;AudioTrack&gt; getAudioTracks(); </span> </td> 
   <td colname="3"> Fournit un  de pistes audio alternatives disponibles. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;AudioTrack&gt; getAudioTracks(); </span> </td> 
   <td colname="3"> <p>Fournit un  de pistes audio alternatives disponibles. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> AudioTrack getSelectedAudioTrack(); </span> </td> 
   <td colname="3"> <p>Récupère la piste audio sélectionnée avec <span class="codeph"> selectAudioTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack ( AudioTrack audioTrack ) </span> </td> 
   <td colname="3"> <p>Sélectionne une piste audio à utiliser comme piste audio actuelle. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Métadonnées minutées</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen hasTimedMetadata(); </span> </td> 
   <td colname="3"> <p>True si le flux est associé à des métadonnées temporisées. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;TimedMetadata&gt; getTimedMetadata(); </span> </td> 
   <td colname="3"> <p>Fournit un des objets de métadonnées minutés associés au flux. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen isDynamic(); </span> </td> 
   <td colname="3"> <p>True si le flux est un flux à débit binaire multiple (MBR). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;&gt; getProfiles(); </span> </td> 
   <td colname="3"> <p>Fournit un  du de débit binaire associé. Pour chaque  de, vous pouvez récupérer son débit ainsi que la hauteur et la largeur du  de. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Trump play</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen isTrickPlaySupported(); </span> </td> 
   <td colname="3"> <p>True si le lecteur prend en charge l’avance rapide, le rembobinage et la reprise. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt; Float&gt; getAvailablePlaybackRates </span> </td> 
   <td colname="3"> <p>Fournit le des taux de lecture disponibles dans le contexte de la fonction de lecture par astuce. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Ressource média</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaResource getResource(); </span> </td> 
   <td colname="3"> <p>Renvoie la ressource média associée à cet élément. </p> </td> 
  </tr> 
 </tbody> 
</table>

