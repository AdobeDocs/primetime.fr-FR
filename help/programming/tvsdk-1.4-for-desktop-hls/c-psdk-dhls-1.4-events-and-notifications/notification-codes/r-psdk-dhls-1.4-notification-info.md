---
description: Ce tableau fournit des informations détaillées sur les notifications de type INFO.
seo-description: Ce tableau fournit des informations détaillées sur les notifications de type INFO.
seo-title: Codes de notification INFO
title: Codes de notification INFO
uuid: 27117707-be3d-4935-a193-85776edd26ce
translation-type: tm+mt
source-git-commit: b9e98ef2b4246fdfd79ebcd91db344c97367d661
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 4%

---


# Codes de notification INFO{#info-notification-codes}

Ce tableau fournit des informations détaillées sur les notifications de type INFO.

## Titre de la section {#section_ED4302E363AE48CBA2C3E0B71AE612D8}

La plupart des notifications d’informations contiennent des métadonnées pertinentes, par exemple l’URL de la ressource qui n’a pas été téléchargée. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans l’autre contenu audio ou dans une publicité.

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
   <td colname="1"><span class="codeph"> 300000  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_DÉBUT  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> La lecture a commencé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300001  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_COMPLETE  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> La lecture est terminée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300002  </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_DÉBUT  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> SEEK_TIME</span> </td> 
   <td colname="5"> Une opération de recherche a été lancée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300003  </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_COMPLETE  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> SEEK_TIME</span> </td> 
   <td colname="5"> Opération de recherche terminée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300004  </span> </td> 
   <td colname="2"><span class="codeph"> CONTENT_CHANGE  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> <span class="codeph"> CONTENT_</span> <span class="codeph"> IDCURRENT_MEDIA_TIME</span> </td> 
   <td colname="5"> Le temps de lecture actuel a franchi la frontière entre le contenu principal et le contenu alternatif. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300005  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYER_STATE_CHANGE  </span> </td> 
   <td colname="3"> <p>Toute notification d’erreur. </p> </td> 
   <td colname="4"><span class="codeph"> ETAT  </span> </td> 
   <td colname="5"> L'état du lecteur a changé. Lorsque l’état est ERROR, la notification interne est l’objet de notification d’erreur qui a déclenché le basculement vers l’état ERROR. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300100  </span> </td> 
   <td colname="2"><span class="codeph"> LOAD_INFO_AVAILABLE  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <span class="codeph"> FRAGMENT_</span> <span class="codeph"> URLFRAGMENT_</span> <span class="codeph"> SIZEFRAGMENT_DOWNLOAD_</span> <span class="codeph"> DURATIONPERIOD_INDEX</span> </td> 
   <td colname="5"> Fournit des informations relatives à la manière dont les segments de vidéo sont téléchargés. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300101  </span> </td> 
   <td colname="2"><span class="codeph"> VIDEO_SIZE_CHANGED  </span> </td> 
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
   <td colname="1"><span class="codeph"> 302000  </span> </td> 
   <td colname="2"><span class="codeph"> BITRATE_CHANGE  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> BITRATE  </span><span class="codeph"> CURRENT_MEDIA_TIME  </span> </td> 
   <td colname="5"> Le débit de la vidéo a changé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Traitement des publicités  </b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303000  </span> </td> 
   <td colname="2"><span class="codeph"> TIMELINE_CHANGE  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID  </span><span class="codeph"> PERIOD_INDEX  </span> </td> 
   <td colname="5"> La chronologie a changé (par exemple, un autre contenu a été ajouté ou supprimé). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303001  </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_ PLACEMENT_COMPLETE  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <span class="codeph"> PROPOSED_AD_</span> <span class="codeph"> BREAKACCEPTED_AD_BREAK</span> </td> 
   <td colname="5"> TVSDK a accepté une coupure publicitaire proposée et l’a placée (en tout ou en partie) sur la chronologie de la lecture. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303002  </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_DÉBUT  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> AD_BREAK  </span> </td> 
   <td colname="5"> La lecture d’une coupure publicitaire particulière a commencé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303003  </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_COMPLETE  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> AD_BREAK  </span> </td> 
   <td colname="5"> La lecture d'une coupure publicitaire particulière est terminée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303004  </span> </td> 
   <td colname="2"><span class="codeph"> AD_DÉBUT  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> </td> 
   <td colname="5"> La lecture d'une publicité particulière a commencé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303005  </span> </td> 
   <td colname="2"><span class="codeph"> AD_COMPLETE  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> </td> 
   <td colname="5"> La lecture d'une publicité particulière est terminée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303006  </span> </td> 
   <td colname="2"><span class="codeph"> AD_PROGRESS  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> <span class="codeph"> PROGRÈS</span> </td> 
   <td colname="5"> La lecture d'une publicité particulière a atteint un certain pourcentage de cette publicité. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Audio à liaison tardive (LBA)</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 304000  </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_CHANGE  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> TRACK_ID  </span><span class="codeph"> CURRENT_MEDIA_TIME  </span> </td> 
   <td colname="5"> <p>La piste audio a changé. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>DRM</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 305000  </span> </td> 
   <td colname="2"><span class="codeph"> DRM_METADATA_AVAILABLE  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> PREFETCH_TIMESTAMP  </span> </td> 
   <td colname="5"> <p>De nouvelles données DRM sont disponibles. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Générique</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 399999  </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_INFO  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <p>Aucun </p> </td> 
   <td colname="5"> <p>Marque un événement d’informations générique. Non pas réellement émis par TVSDK. Il ne s’agit que d’un marqueur pour la fin de la plage de codes numériques correspondant aux événements d’information TVSDK. </p> </td> 
  </tr> 
 </tbody> 
</table>

