---
description: Votre application peut surveiller l’activité de votre lecteur et le changement d’état du lecteur en écoutant les événements distribués par TVSDK.
title: Événements de lecture
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# Événements de lecture {#playback-events}

Votre application peut surveiller l’activité de votre lecteur et le changement d’état du lecteur en écoutant les événements distribués par TVSDK.

TVSDK distribue des événements de lecture lorsque des opérations de lecture multimédia se produisent, par exemple lorsqu’une vidéo commence à être lue. Pour être averti de tous les événements liés à la lecture, enregistrez les écouteurs auprès de la fonction `MediaPlayer` pour les événements suivants.

<table frame="all" colsep="1" rowsep="1" id="table_922EEA3DE0BD47BA982E11F890CA0A6B"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Événement </th> 
   <th colname="2" class="entry"> Signification </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>Lecture</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">PlaybackRateEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html#RATE_SELECTED" format="html" scope="external"> RATE_SELECTED</a> </td> 
   <td colname="2"> L’utilisateur ou TVSDK a sélectionné un nouveau taux de lecture, tel qu’une lecture anticipée, un retour arrière ou une reprise à une vitesse normale. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">PlaybackRateEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html#RATE_PLAYING" format="html" scope="external"> RATE_PLAYING</a> </td> 
   <td colname="2"> Un nouveau taux de lecture est visible à l’écran. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> TimeChangeEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimeChangeEvent.html#TIME_CHANGED" format="html" scope="external"> TIME_CHANGED</a> </td> 
   <td colname="2"> La position actuelle du curseur de lecture du média a changé. Distribué régulièrement lorsque l’heure actuelle a changé, toutes les 250 ms ou plus. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Lecteur multimédia</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">MediaPlayerStatus ChangeEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerStatusChangeEvent.html#STATUS_CHANGED" format="html" scope="external"> STATUS_CHANGED</a> </td> 
   <td colname="2"> L’état du lecteur multimédia a changé. Votre application doit gérer les erreurs dans le rappel de cet événement. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">ProfileEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/ProfileEvent.html#PROFILE_CHANGED" format="html" scope="external"> PROFILE_CHANGED</a> </td> 
   <td colname="2">Le profil actuel du lecteur multimédia a changé. Utilisez la variable <span class="codeph"> ProfileEvent.profile</span> pour obtenir le nouveau profil en cours de lecture. Utilisez la variable <span class="codeph"> time</span> pour obtenir l’heure à laquelle cet événement s’est produit. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>MediaplayerItem</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">Événement MediaPlayerItem.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#ITEM_CREATED" format="html" scope="external"> ITEMENT_CREATED</a> </td> 
   <td colname="2">A <span class="codeph"> MediaPlayerItem</span> a été créé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">Événement MediaPlayerItem.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#ITEM_UPDATED" format="html" scope="external"> ITEMENT_UPDATED</a> </td> 
   <td colname="2">Le lecteur multimédia a correctement mis à jour le média dans l’un de ces cas : 
    <ul id="ul_E4D1A1D468544C3B9F8046E9B68A956D"> 
     <li id="li_35A2A417BF924E039D9CB36CFBCDFEB6">Lorsqu’une actualisation du manifeste se produit pour une ressource active. </li> 
     <li id="li_E7AB380C212B4011B07C3B313282681C">Lorsqu’une ressource VOD ou active comporte un sous-titrage codé et que l’activité est d’abord découverte pour une piste de sous-titrage codé. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Sous-titres et audio</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Événement MediaPlayerItem.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#CAPTION_UPDATED" format="html" scope="external"> CAPTION_UPDATED</a> </td> 
   <td colname="2">Une nouvelle piste de sous-titrage a été détectée dans le flux multimédia et le <span class="codeph"> closedCaptionsTracks</span> La collection a été mise à jour. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Manifeste et journal</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="0"> 
   <td colname="1">TimelineEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED" format="html" scope="external"> TIMELINE_UPDATED</a> </td> 
   <td colname="2">Le lecteur multimédia a ajouté ou supprimé des publicités ; il dispose donc d’une chronologie mise à jour. <p>Le manifeste actualisé pour une ressource en direct et les anciennes coupures publicitaires ont été supprimées de la chronologie ou de nouvelles opportunités publicitaires (repères) ont été découvertes. Le lecteur multimédia tente de résoudre et de placer de nouvelles publicités dans la chronologie. </p> <p> Utilisez cet événement pour vérifier si la chronologie comporte des mises à jour (VOD ne change pas pendant la lecture). Vous pouvez ensuite récupérer la chronologie à l’aide de <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayer.html#timeline" format="html" scope="external"> MediaPlayer.timeline</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>
