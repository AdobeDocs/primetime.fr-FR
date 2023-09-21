---
description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
title: Méthodes MediaPlayerItem pour accéder aux informations MediaResource
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# Méthodes MediaPlayerItem pour accéder aux informations MediaResource {#mediaplayeritem-methods-for-accessing-mediaresource-information}

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
   <td colname="2"> <span class="codeph"> Liste&lt;string&gt; getAdTags() </span> </td> 
   <td colname="3"> Fournit la liste des balises d’annonce utilisées pour le processus d’emplacement des publicités. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Flux en direct</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isLive(); </span> </td> 
   <td colname="3"> True si le flux est actif ; false s’il est VOD. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>DRM protégé</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isProtected(); </span> </td> 
   <td colname="3"> True si le flux est protégé par DRM. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;drmmetadatainfo&gt; getDRMMetadataInfos(); </span> </td> 
   <td colname="3"> Répertorie tous les objets de métadonnées DRM découverts dans le manifeste. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Sous-titres codés</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasClosedCaptions(); </span> </td> 
   <td colname="3"> True si des pistes de sous-titres sont disponibles. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;closedcaptionstrack&gt; getClosedCationsTracks(); </span> </td> 
   <td colname="3"> Fournit une liste des suivis de sous-titres disponibles. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); </span> </td> 
   <td colname="3"> Récupère le suivi actuel des sous-titres sélectionnés avec <span class="codeph"> SelectClosedCaptionsTrack </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack) </span> </td> 
   <td colname="3"> Définit un suivi de sous-titres comme suivi de sous-titres fermés actuel. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Autres pistes audio</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasAlternateAudio(); </span> </td> 
   <td colname="3"> True si le flux comporte des pistes audio alternatives. <p>Remarque : La piste audio principale (par défaut) fait également partie de la liste de piste audio alternative. </p> <p>TVSDK pour Android considère la piste audio principale comme l’un des éléments de la liste de piste audio alternative. Pour cette raison, le seul cas où <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> La valeur false est renvoyée lorsque le flux n’a aucun son. Si le contenu ne comporte qu’une seule piste audio, cette méthode renvoie la valeur true et <span class="codeph"> MediaPlayerItem.getAudioTracks </span> renvoie une liste avec un seul élément (la piste audio par défaut). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;audiotrack&gt; getAudioTracks(); </span> </td> 
   <td colname="3"> Fournit une liste des pistes audio secondaires disponibles. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> AudioTrack getSelectedAudioTrack(); </span> </td> 
   <td colname="3"> Récupère la piste audio sélectionnée avec <span class="codeph"> selectAudioTrack </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack ( AudioTrack audioTrack ) </span> </td> 
   <td colname="3"> Permet de sélectionner une piste audio comme piste audio actuelle. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Métadonnées minutées</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen hasTimedMetadata(); </span> </td> 
   <td colname="3"> True si le flux a associé des métadonnées minutées. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;timedmetadata&gt; getTimedMetadata(); </span> </td> 
   <td colname="3"> Fournit une liste des objets de métadonnées minutés associés au flux. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Profils multiples (débit)</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isDynamic(); </span> </td> 
   <td colname="3"> True si le flux est un flux à débit multiple (MBR). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;profile&gt; getProfiles(); </span> </td> 
   <td colname="3"> Fournit une liste des profils de débit associés. Pour chaque profil, vous pouvez récupérer son débit ainsi que la hauteur et la largeur du profil. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Profile getSelectedProfile() </span> </td> 
   <td colname="3"> Récupère le profil actuellement sélectionné. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Lecture de piste</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen isTrickPlaySupported(); </span> </td> 
   <td colname="3"> True si le lecteur prend en charge l’avance rapide, le retour arrière et la reprise. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt; float&gt; getAvailablePlaybackRates() </span> </td> 
   <td colname="3"> Fournit la liste des taux de lecture disponibles dans le contexte de la fonction de lecture de l’astuce. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Float getSelectedPlaybackRate() </span> </td> 
   <td colname="3"> Récupère le taux de lecture actuellement sélectionné. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaPlayerItemConfig getConfig() </span> </td> 
   <td colname="3"> Renvoie la variable <span class="codeph"> MediaPlayerItemConfig </span> instance associée à cet élément. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>Ressource multimédia</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaResource getResource(); </span> </td> 
   <td colname="3"> Renvoie la ressource multimédia associée à cet élément. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> int getResourceId() </span> </td> 
   <td colname="3"> Renvoie l’identifiant du média associé à cet élément. Cet identifiant est défini lorsque l’élément est chargé à l’aide de <span class="codeph"> MediaPlayerItemLoader.load </span>. </td> 
  </tr> 
 </tbody> 
</table>
