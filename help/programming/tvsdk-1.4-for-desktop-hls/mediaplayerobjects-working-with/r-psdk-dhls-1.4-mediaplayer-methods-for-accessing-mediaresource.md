---
description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
seo-description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
seo-title: Méthodes MediaPlayer pour l’accès aux informations MediaResource
title: Méthodes MediaPlayer pour l’accès aux informations MediaResource
uuid: c2d18f8e-4107-42bc-a975-9b881aadd27b
translation-type: tm+mt
source-git-commit: b9e98ef2b4246fdfd79ebcd91db344c97367d661

---


# Méthodes MediaPlayer pour l’accès aux informations MediaResource{#mediaplayer-methods-for-accessing-mediaresource-information}

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
   <td colname="1"> <b>Flux en direct </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get isLive():Boolean; </span> </td> 
   <td colname="3"> <p>True si le flux est actif ; false s’il s’agit de VOD. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>DRM protégé</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get isProtected():Boolean; </span> </td> 
   <td colname="3"> <p>True si le flux est protégé par DRM. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> fonction get drmMetadataInfos() : Vecteur.&lt;DRMMetadataInfo&gt;; </span> </td> 
   <td colname="3"> <p>Liste tous les objets de métadonnées DRM découverts dans le manifeste. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Sous-titres</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> getClosedCaptions():Boolean; </span> </td> 
   <td colname="3"> <p>True si des pistes de sous-titrage sont disponibles. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get closeCaptionsTracks():Vector.&lt;ClosedCaptionsTrack&gt;; </span> </td> 
   <td colname="3"> <p>Fournit une liste de pistes de sous-titres disponibles. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get selectedClosedCaptionsTrack():ClosedCaptionsTrack </span> </td> 
   <td colname="3"> <p>Récupère le suivi de sous-titrage actuel sélectionné avec <span class="codeph"> SelectClosedCaptionsTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack (closeCaptionsTrack: com.adobe.mediacore.info:ClosedCaptionsTrack ) </span> </td> 
   <td colname="3"> <p>Définit une piste de sous-titrage fermée comme piste de sous-titrage fermée actuelle. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Autres pistes audio </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> getAlternateAudio():Boolean; </span> </td> 
   <td colname="3"> <p>True si le flux comporte d’autres pistes audio. </p> <p>Conseil :  La piste audio principale (par défaut) fait également partie de la liste de piste audio alternative. </p> <p>TVSDK for Desktop HLS considère que la piste audio principale est l’un des éléments de la liste de piste audio alternative. C’est pourquoi le seul cas où <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> renvoie false est celui où le flux ne comporte pas d’audio. Si le contenu ne comporte qu’une seule piste audio, cette méthode renvoie true et <span class="codeph"> l’option AudioTracks </span> renvoie une liste avec un seul élément (la piste audio par défaut). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get audioTracks():Vector.&lt;AudioTrack&gt;; </span> </td> 
   <td colname="3"> Fournit une liste de pistes audio alternatives disponibles. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get audioTracks():Vector.&lt;AudioTrack&gt;; </span> </td> 
   <td colname="3"> <p>Fournit une liste de pistes audio alternatives disponibles. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get selectedAudioTrack():AudioTrack; </span> </td> 
   <td colname="3"> <p>Récupère la piste audio sélectionnée avec <span class="codeph"> select AudioTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack(audioTrack: AudioTrack ) </span> </td> 
   <td colname="3"> <p>Sélectionne une piste audio à utiliser comme piste audio actuelle. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Métadonnées minutées</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> getTimedMetadata():Boolean; </span> </td> 
   <td colname="3"> <p>True si le flux est associé à des métadonnées temporisées. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get timedMetadata():Vector.&lt;TimedMetadata&gt;; </span> </td> 
   <td colname="3"> <p>Fournit une liste des objets de métadonnées minutés associés au flux. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get isDynamic():Boolean; </span> </td> 
   <td colname="3"> <p>True si le flux est un flux à débit binaire multiple (MBR). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get profils():Vector.&lt;Profil&gt;; </span> </td> 
   <td colname="3"> <p>Fournit une liste des profils de débit binaire associés. Pour chaque profil, vous pouvez récupérer son débit ainsi que la hauteur et la largeur du profil. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Jeu de cartes </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get isTrickPlaySupported():Boolean; </span> </td> 
   <td colname="3"> <p>True si le lecteur prend en charge l’avance rapide, le rembobinage et la reprise. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get availablePlaybackRates():Vector.&lt;Nombre&gt; </span> </td> 
   <td colname="3"> <p>Fournit la liste des taux de lecture disponibles dans le contexte de la fonction de lecture par astuces. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Lecteur multimédia </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> fonction get player():MediaPlayer </span> </td> 
   <td colname="3"> <p>Renvoie le lecteur de médias actuellement associé à ce lecteur. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Ressource média</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get resource():MediaResource; </span> </td> 
   <td colname="3"> <p>Renvoie la ressource média associée à cet élément. </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> function get resourceId():int </span> </td> 
   <td colname="3"> <p>Renvoie l'identifiant de média associé à cet élément. </p> </td> 
  </tr> 
 </tbody> 
</table>

