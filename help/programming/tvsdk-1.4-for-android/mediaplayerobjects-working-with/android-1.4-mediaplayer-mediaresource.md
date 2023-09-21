---
description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
title: Méthodes MediaPlayer pour accéder aux informations MediaResource
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

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
   <td colname="2"> <span class="codeph"> Liste&lt;string&gt; getAdTags() </span> </td> 
   <td colname="3"> <p>Fournit la liste des balises d’annonce utilisées pour le processus d’emplacement des publicités. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Flux en direct</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isLive(); </span> </td> 
   <td colname="3"> <p>True si le flux est actif ; false s’il est VOD. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>DRM protégé</b> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isProtected(); </span> </td> 
   <td colname="3"> <p>True si le flux est protégé par DRM. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;drmmetadatainfo&gt; getDRMMetadataInfos(); </span> </td> 
   <td colname="3"> <p>Répertorie tous les objets de métadonnées DRM découverts dans le manifeste. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Sous-titres codés</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasClosedCaptions(); </span> </td> 
   <td colname="3"> <p>True si des pistes de sous-titres sont disponibles. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;closedcaptionstrack&gt; getClosedCationsTracks(); </span> </td> 
   <td colname="3"> <p>Fournit une liste des suivis de sous-titres disponibles. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); </span> </td> 
   <td colname="3"> <p>Récupère le suivi actuel des sous-titres sélectionnés avec <span class="codeph"> SelectClosedCaptionsTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack) </span> </td> 
   <td colname="3"> <p>Définit un suivi de sous-titres comme suivi de sous-titres fermés actuel. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Autres pistes audio</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasAlternateAudio(); </span> </td> 
   <td colname="3"> <p>True si le flux comporte des pistes audio alternatives. </p> <p>Conseil : La piste audio principale (par défaut) fait également partie de la liste de piste audio alternative. </p> <p>TVSDK pour Android considère la piste audio principale comme l’un des éléments de la liste de piste audio alternative. Pour cette raison, le seul cas où <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> La valeur false est renvoyée lorsque le flux n’a aucun son. Si le contenu ne comporte qu’une seule piste audio, cette méthode renvoie la valeur true et <span class="codeph"> MediaPlayerItem.getAudioTracks </span> renvoie une liste avec un seul élément (la piste audio par défaut). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;audiotrack&gt; getAudioTracks(); </span> </td> 
   <td colname="3"> Fournit une liste des pistes audio secondaires disponibles. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;audiotrack&gt; getAudioTracks(); </span> </td> 
   <td colname="3"> <p>Fournit une liste des pistes audio secondaires disponibles. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> AudioTrack getSelectedAudioTrack(); </span> </td> 
   <td colname="3"> <p>Récupère la piste audio sélectionnée avec <span class="codeph"> selectAudioTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack ( AudioTrack audioTrack ) </span> </td> 
   <td colname="3"> <p>Permet de sélectionner une piste audio comme piste audio actuelle. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Métadonnées minutées</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen hasTimedMetadata(); </span> </td> 
   <td colname="3"> <p>True si le flux a associé des métadonnées minutées. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;timedmetadata&gt; getTimedMetadata(); </span> </td> 
   <td colname="3"> <p>Fournit une liste des objets de métadonnées minutés associés au flux. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isDynamic(); </span> </td> 
   <td colname="3"> <p>True si le flux est un flux à débit multiple (MBR). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt;profile&gt; getProfiles(); </span> </td> 
   <td colname="3"> <p>Fournit une liste des profils de débit associés. Pour chaque profil, vous pouvez récupérer son débit ainsi que la hauteur et la largeur du profil. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Lecture de piste</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> booléen isTrickPlaySupported(); </span> </td> 
   <td colname="3"> <p>True si le lecteur prend en charge l’avance rapide, le retour arrière et la reprise. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Liste&lt; float&gt; getAvailablePlaybackRates </span> </td> 
   <td colname="3"> <p>Fournit la liste des taux de lecture disponibles dans le contexte de la fonction de lecture de l’astuce. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Ressource multimédia</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaResource getResource(); </span> </td> 
   <td colname="3"> <p>Renvoie la ressource multimédia associée à cet élément. </p> </td> 
  </tr> 
 </tbody> 
</table>
