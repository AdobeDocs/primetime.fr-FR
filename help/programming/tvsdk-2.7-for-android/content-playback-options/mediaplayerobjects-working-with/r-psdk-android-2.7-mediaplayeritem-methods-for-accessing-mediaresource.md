---
description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
seo-description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
seo-title: Méthodes MediaPlayerItem pour l’accès aux informations MediaResource
title: Méthodes MediaPlayerItem pour l’accès aux informations MediaResource
uuid: c6e77eb7-cefd-48aa-9373-2b44a96217a5
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Méthodes MediaPlayerItem pour l’accès aux informations MediaResource {#mediaplayeritem-methods-for-accessing-mediaresource-information}

Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.

<table frame="all" colsep="1" rowsep="1" id="table_F6006A9167044AC087A6ECB20B8CCD5D"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="2" class="entry"> Méthode </th> 
   <th colname="3" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Balises publicitaires</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;String&gt; getAdTags() </span> </td> 
   <td colname="3"> Fournit le des balises publicitaires utilisées pour le processus d’emplacement des publicités. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Flux en direct</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen isLive(); </span> </td> 
   <td colname="3"> True si le flux est en direct ; false s’il s’agit de VOD. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>DRM protégé</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen isProtected(); </span> </td> 
   <td colname="3"> True si le flux est protégé par DRM. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;DRMMetadataInfo&gt; getDRMMetadataInfos(); </span> </td> 
   <td colname="3"> tous les objets de métadonnées DRM découverts dans le manifeste. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Sous-titres</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen hasClosedCaptions(); </span> </td> 
   <td colname="3"> True si des pistes de sous-titrage sont disponibles. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;ClosedCaptionsTrack&gt; getClosedCationsTracks(); </span> </td> 
   <td colname="3"> Fournit un  de pistes de sous-titrage codé disponibles. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); </span> </td> 
   <td colname="3"> Récupère la piste de sous-titrage codée actuelle sélectionnée avec <span class="codeph"> SelectClosedCaptionsTrack </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack ( ClosedCaptionsTrack closeCaptionsTrack) </span> </td> 
   <td colname="3"> Définit une piste de sous-titrage codé comme la piste de sous-titrage codé actuelle. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Autres pistes audio</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen hasAlternateAudio(); </span> </td> 
   <td colname="3"> True si le flux comporte des pistes audio de remplacement. <p>Remarque :  La piste audio principale (par défaut) fait également partie du de piste audio alternatif. </p> <p>TVSDK pour Android considère la piste audio principale comme l’un des éléments du de piste audio alternatif. Pour cette raison, le seul cas où <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> renvoie false est le cas lorsque le flux n’a pas du tout d’audio. Si le contenu ne comporte qu’une seule piste audio, cette méthode renvoie true et <span class="codeph"> MediaPlayerItem.getAudioTracks </span> renvoie un avec un seul élément (la piste audio par défaut). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;AudioTrack&gt; getAudioTracks(); </span> </td> 
   <td colname="3"> Fournit un  de pistes audio alternatives disponibles. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> AudioTrack getSelectedAudioTrack(); </span> </td> 
   <td colname="3"> Récupère la piste audio sélectionnée avec <span class="codeph"> selectAudioTrack </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack ( AudioTrack audioTrack ) </span> </td> 
   <td colname="3"> Sélectionne une piste audio à utiliser comme piste audio actuelle. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Métadonnées minutées</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen hasTimedMetadata(); </span> </td> 
   <td colname="3"> True si le flux est associé à des métadonnées temporisées. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;TimedMetadata&gt; getTimedMetadata(); </span> </td> 
   <td colname="3"> Fournit un des objets de métadonnées minutés associés au flux. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>multiples (débit)</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen isDynamic(); </span> </td> 
   <td colname="3"> True si le flux est un flux à débit binaire multiple (MBR). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;&gt; getProfiles(); </span> </td> 
   <td colname="3"> Fournit un  du de débit binaire associé. Pour chaque  de, vous pouvez récupérer son débit ainsi que la hauteur et la largeur du  de. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> getSelectedProfile() </span> </td> 
   <td colname="3"> Récupère le  actuellement sélectionné. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Trump play</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen isTrickPlaySupported(); </span> </td> 
   <td colname="3"> True si le lecteur prend en charge l’avance rapide, le rembobinage et la reprise. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt; Float&gt; getAvailablePlaybackRates() </span> </td> 
   <td colname="3"> Fournit le des taux de lecture disponibles dans le contexte de la fonction de lecture par astuce. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Float getSelectedPlaybackRate() </span> </td> 
   <td colname="3"> Récupère le taux de lecture actuellement sélectionné. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaPlayerItemConfig getConfig() </span> </td> 
   <td colname="3"> Renvoie l’ <span class="codeph"> instance MediaPlayerItemConfig </span> associée à cet élément. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Ressource média</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaResource getResource(); </span> </td> 
   <td colname="3"> Renvoie la ressource média associée à cet élément. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> int getResourceId() </span> </td> 
   <td colname="3"> Renvoie l’identifiant de média associé à cet élément. Cet ID est défini lorsque l’élément est chargé à l’aide de <span class="codeph"> MediaPlayerItemLoader.load </span>. </td> 
  </tr> 
 </tbody> 
</table>
