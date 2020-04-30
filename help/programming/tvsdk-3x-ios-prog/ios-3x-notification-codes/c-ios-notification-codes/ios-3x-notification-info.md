---
description: Ce tableau fournit des informations détaillées sur les notifications de type INFO.
seo-description: Ce tableau fournit des informations détaillées sur les notifications de type INFO.
seo-title: Codes de notification INFO
title: Codes de notification INFO
uuid: 21297863-dac1-45a4-ac9d-309d1f746f8b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Codes de notification INFO {#info-notification-codes}

Ce tableau fournit des informations détaillées sur les notifications de type INFO.

La plupart des notifications d’informations contiennent des métadonnées pertinentes, par exemple l’URL de la ressource qui n’a pas été téléchargée. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans l’autre contenu audio ou dans une publicité.

<table frame="all" colsep="1" rowsep="1" id="table_503463046E764A87B10EB5D8B294EB23"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>Code</b></th> 
   <th colname="2" class="entry"><b>Nom</b></th> 
   <th colname="3" class="entry"><b>Notification interne</b></th> 
   <th colname="4" class="entry"><b>Touches de métadonnées</b></th> 
   <th colname="5" class="entry"><b>Commentaires</b></th> 
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
   <td colname="2"><span class="codeph"> PLAYBACK_DÉBUT </span> </td> 
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
   <td colname="2"><span class="codeph"> SEEK_DÉBUT </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> <p> Aucun </p> </td> 
   <td colname="5"> Une opération de recherche a été lancée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300003 </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_COMPLETE </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> <p>Aucun </p> </td> 
   <td colname="5"> Opération de recherche terminée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300005 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYER_STATE_CHANGE </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <p>Aucun </p> </td> 
   <td colname="5"> L'état du lecteur a changé. Lorsque l’état est ERROR, la notification interne est l’objet de notification d’erreur qui a déclenché le basculement vers l’état ERROR. </td> 
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
   <td colname="4"><span class="codeph"> BITRAGE </span> </td> 
   <td colname="5"> Le débit de la vidéo a changé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Audio à liaison tardive (LBA)</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 304000 </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_CHANGE </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <p>Aucun </p> </td> 
   <td colname="5"> <p>La piste audio a changé. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Sous-titres</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 307000 </span> </td> 
   <td colname="2"><span class="codeph"> SUBTITLES_TRACK_CHANGE </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <p>Aucun </p> </td> 
   <td colname="5"> <p>Le suivi des sous-titres a changé. </p> </td> 
  </tr> 
 </tbody> 
</table>