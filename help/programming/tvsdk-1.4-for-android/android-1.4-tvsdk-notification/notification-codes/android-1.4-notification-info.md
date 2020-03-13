---
description: Ce tableau fournit des informations détaillées sur INFO. notifications de type.
seo-description: Ce tableau fournit des informations détaillées sur INFO. notifications de type.
seo-title: Codes de notification INFO
title: Codes de notification INFO
uuid: 2b9f9328-4e09-44b7-8ea5-237c46e65e73
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Codes de notification INFO{#info-notification-codes}

Ce tableau fournit des informations détaillées sur INFO. notifications de type.

<!--<a id="section_ED4302E363AE48CBA2C3E0B71AE612D8"></a>-->

La plupart des notifications d’informations contiennent des métadonnées appropriées, par exemple l’URL de la ressource qui n’a pas été téléchargée. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans le contenu audio alternatif ou dans une publicité.

<table frame="all" colsep="1" rowsep="1" id="table_503463046E764A87B10EB5D8B294EB23"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Code </th> 
   <th colname="2" class="entry"> Nom </th> 
   <th colname="3" class="entry"> Notification interne </th> 
   <th colname="4" class="entry"> Touches de métadonnées </th> 
   <th colname="5" class="entry"> Commentaires </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>Lecture</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300000 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_ </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> La lecture a commencé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300001 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_COMPLETE </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> La lecture est terminée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300002 </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_ </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> SEEK_TIME</span> </td> 
   <td colname="5"> Une opération de recherche a été initiée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300003 </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_COMPLETE </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> SEEK_TIME</span> </td> 
   <td colname="5"> Opération de recherche terminée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300004 </span> </td> 
   <td colname="2"><span class="codeph"> CONTENT_CHANGE </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> <span class="codeph"> CONTENT_ID</span><span class="codeph"> CURRENT_MEDIA_TIME</span> </td> 
   <td colname="5"> Le temps de lecture actuel a franchi la frontière entre le contenu principal et le contenu alternatif. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300005 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYER_STATE_CHANGE </span> </td> 
   <td colname="3"> <p>Toute notification d’erreur. </p> </td> 
   <td colname="4"><span class="codeph"> ETAT </span> </td> 
   <td colname="5"> L’état du lecteur a changé. Lorsque l’état est ERROR, la notification interne est l’objet de notification d’erreur qui a déclenché le basculement vers l’état ERROR. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300006 </span> </td> 
   <td colname="2"><span class="codeph"> CONTENT_MARKER </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID CURRENT_MEDIA_TIME </span> </td> 
   <td colname="5"> Marqueur de contenu reçu. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300100 </span> </td> 
   <td colname="2"><span class="codeph"> LOAD_INFO_AVAILABLE </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <span class="codeph"> FRAGMENT_URL</span> <span class="codeph"> FRAGMENT_SIZE</span> FRAGMENT_DOWNLOAD_DURATION <span class="codeph"></span> <span class="codeph"> PERIOD_INDEX</span> </td> 
   <td colname="5"> Fournit des informations relatives à la manière dont les segments de vidéo sont téléchargés. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300101 </span> </td> 
   <td colname="2"><span class="codeph"> VIDEO_SIZE_CHANGED </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <span class="codeph"> HAUTEUR</span> <p><span class="codeph"> LARGEUR</span> </p> </td> 
   <td colname="5"> La taille de la fenêtre de lecture vidéo a changé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Débit adaptatif (ABR)</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 302000 </span> </td> 
   <td colname="2"><span class="codeph"> BITRATE_CHANGE </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> BITRATE </span><span class="codeph"> CURRENT_MEDIA_TIME </span> </td> 
   <td colname="5"> Le débit de la vidéo a changé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Traitement des publicités</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303000 </span> </td> 
   <td colname="2"><span class="codeph"> TIMELINE_CHANGE </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID </span><span class="codeph"> PERIOD_INDEX </span> </td> 
   <td colname="5"> La chronologie a changé (par exemple, un autre contenu a été ajouté ou supprimé). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303001 </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_PLACEMENT_COMPLETE </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <span class="codeph"> PROPOSED_AD_BREAK</span><span class="codeph"> ACCEPTED_AD_BREAK</span> </td> 
   <td colname="5"> Une coupure publicitaire proposée a été acceptée par <code>primetime-sdk-name</code> et placée (en tout ou en partie) sur la chronologie de la lecture. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303002 </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_ </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> AD_BREAK </span> </td> 
   <td colname="5"> La lecture d’une coupure publicitaire particulière a commencé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303003 </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_COMPLETE </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> AD_BREAK </span> </td> 
   <td colname="5"> La lecture d'une coupure publicitaire particulière est terminée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303004 </span> </td> 
   <td colname="2"><span class="codeph"> AD_ </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> </td> 
   <td colname="5"> La lecture d'une publicité particulière a commencé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303005 </span> </td> 
   <td colname="2"><span class="codeph"> AD_COMPLETE </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> </td> 
   <td colname="5"> La lecture d'une publicité particulière est terminée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303006 </span> </td> 
   <td colname="2"><span class="codeph"> AD_PROGRESS </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> <span class="codeph"> PROGRÈS</span> </td> 
   <td colname="5"> La lecture d'une publicité particulière a atteint un certain pourcentage de cette publicité. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303007 </span> </td> 
   <td colname="2"><span class="codeph"> TIMED_METADATA_AJOUTER </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <span class="codeph"> TYPE</span> <p><span class="codeph"> ID</span> </p> <span class="codeph"> NOM</span> <p><span class="codeph"> HEURE</span> </p> </td> 
   <td colname="5"> Une nouvelle métadonnée minutée a été découverte dans le manifeste. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303008 </span> </td> 
   <td colname="2"><span class="codeph"> AD_CLICK </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> <span class="codeph"> AD_CLICK</span> </td> 
   <td colname="5"> Renvoie des informations sur une publicité sur laquelle l’utilisateur a cliqué. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303009</span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_SKIPPED</span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> <span class="codeph"> AD_CLICK</span> </td> 
   <td colname="5"> Une coupure publicitaire a été ignorée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname=""><b>Audio à liaison tardive (LBA)</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 304000 </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_CHANGE </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> TRACK_ID </span><span class="codeph"> CURRENT_MEDIA_TIME </span> </td> 
   <td colname="5"> La piste audio a changé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>DRM</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 305000 </span> </td> 
   <td colname="2"><span class="codeph"> DRM_METADATA_AVAILABLE </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> PREFETCH_TIMESTAMP </span> </td> 
   <td colname="5"> De nouvelles données DRM sont disponibles. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Générique</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 399999 </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_INFO </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <p>Aucun </p> </td> 
   <td colname="5"> <p>Marque un  d’informations générique. Non pas réellement émis par TVSDK. C'est juste un marqueur pour la fin de la plage de codes numériques correspondant aux  d'information TVSDK. </p> </td> 
  </tr> 
 </tbody> 
</table>

