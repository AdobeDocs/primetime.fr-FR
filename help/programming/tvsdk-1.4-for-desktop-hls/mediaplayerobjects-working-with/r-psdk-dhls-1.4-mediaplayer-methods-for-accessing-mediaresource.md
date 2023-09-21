---
description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
title: Méthodes MediaPlayer pour accéder aux informations MediaResource
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '449'
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
   <td colname="1"> <b>Flux en direct </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> fonction get isLive():Boolean; </span> </td> 
   <td colname="3"> <p>True si le flux est actif ; false s’il est VOD. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>DRM protégé</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> fonction get isProtected():Boolean; </span> </td> 
   <td colname="3"> <p>True si le flux est protégé par DRM. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> fonction get drmMetadataInfos() : vecteur.&lt;drmmetadatainfo&gt;; </span> </td> 
   <td colname="3"> <p>Répertorie tous les objets de métadonnées DRM découverts dans le manifeste. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Sous-titres codés</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> fonction gethasClosedCaptions():Boolean; </span> </td> 
   <td colname="3"> <p>True si des pistes de sous-titres sont disponibles. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> fonction get closedCaptionsTracks():Vector.&lt;closedcaptionstrack&gt;; </span> </td> 
   <td colname="3"> <p>Fournit une liste des suivis de sous-titres disponibles. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> getClosedCaptionsTrack():ClosedCaptionsTrack </span> </td> 
   <td colname="3"> <p>Récupère le suivi actuel des sous-titres sélectionnés avec <span class="codeph"> SelectClosedCaptionsTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack (closedCaptionsTrack: com.adobe.mediacore.info:ClosedCaptionsTrack ) </span> </td> 
   <td colname="3"> <p>Définit un suivi de sous-titres comme suivi de sous-titres fermés actuel. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Autres pistes audio </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> getAlternateAudio():Boolean; </span> </td> 
   <td colname="3"> <p>True si le flux comporte des pistes audio alternatives. </p> <p>Conseil : La piste audio principale (par défaut) fait également partie de la liste de piste audio alternative. </p> <p>TVSDK pour Desktop HLS considère la piste audio principale comme l’un des éléments de la liste de suivi audio alternative. Pour cette raison, le seul cas où <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> La valeur false est renvoyée lorsque le flux n’a aucun son. Si le contenu ne comporte qu’une seule piste audio, cette méthode renvoie la valeur true et <span class="codeph"> get AudioTracks </span> renvoie une liste avec un seul élément (la piste audio par défaut). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get audioTracks():Vector.&lt;audiotrack&gt;; </span> </td> 
   <td colname="3"> Fournit une liste des pistes audio secondaires disponibles. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get audioTracks():Vector.&lt;audiotrack&gt;; </span> </td> 
   <td colname="3"> <p>Fournit une liste des pistes audio secondaires disponibles. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get selectedAudioTrack():AudioTrack; </span> </td> 
   <td colname="3"> <p>Récupère la piste audio sélectionnée avec <span class="codeph"> selectAudioTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack(audioTrack: AudioTrack ) </span> </td> 
   <td colname="3"> <p>Permet de sélectionner une piste audio comme piste audio actuelle. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Métadonnées minutées</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> fonction gethasTimedMetadata():Boolean; </span> </td> 
   <td colname="3"> <p>True si le flux a associé des métadonnées minutées. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get timedMetadata():Vector.&lt;timedmetadata&gt;; </span> </td> 
   <td colname="3"> <p>Fournit une liste des objets de métadonnées minutés associés au flux. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> fonction get isDynamic():Boolean; </span> </td> 
   <td colname="3"> <p>True si le flux est un flux à débit multiple (MBR). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get profiles():Vector.&lt;profile&gt;; </span> </td> 
   <td colname="3"> <p>Fournit une liste des profils de débit associés. Pour chaque profil, vous pouvez récupérer son débit ainsi que la hauteur et la largeur du profil. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Lecture de piste </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> fonction get isTrickPlaySupported():Boolean; </span> </td> 
   <td colname="3"> <p>True si le lecteur prend en charge l’avance rapide, le retour arrière et la reprise. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> get availablePlaybackRates():Vector.&lt;Number&gt; </span> </td> 
   <td colname="3"> <p>Fournit la liste des taux de lecture disponibles dans le contexte de la fonction de lecture de l’astuce. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Lecteur multimédia </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> fonction get player():MediaPlayer </span> </td> 
   <td colname="3"> <p>Renvoie le lecteur multimédia actuellement associé à ce lecteur. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Ressource multimédia</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> fonction get resource():MediaResource; </span> </td> 
   <td colname="3"> <p>Renvoie la ressource multimédia associée à cet élément. </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> fonction get resourceId():int </span> </td> 
   <td colname="3"> <p>Renvoie l’identifiant du média associé à cet élément. </p> </td> 
  </tr> 
 </tbody> 
</table>
