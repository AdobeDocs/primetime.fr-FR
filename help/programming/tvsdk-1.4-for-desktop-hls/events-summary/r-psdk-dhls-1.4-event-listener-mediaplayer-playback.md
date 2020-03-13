---
description: Votre application peut surveiller le   dans votre lecteur et l’état changeant du lecteur en écoutant les  distribués par TVSDK.
seo-description: Votre application peut surveiller le   dans votre lecteur et l’état changeant du lecteur en écoutant les  distribués par TVSDK.
seo-title: 'de lecture '
title: 'de lecture '
uuid: 6d6491d7-cf25-4130-8388-68b8c028bb71
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# de lecture {#playback-events}

Votre application peut surveiller le   dans votre lecteur et l’état changeant du lecteur en écoutant les  distribués par TVSDK.

TVSDK distribue des de lecture lorsque des opérations de lecture multimédia se produisent, comme le démarrage de la lecture d’une vidéo. Pour être averti de tous les  de lecture, enregistrez les écouteurs avec l’ `MediaPlayer` objet pour le  suivant.

<table frame="all" colsep="1" rowsep="1" id="table_922EEA3DE0BD47BA982E11F890CA0A6B"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry">  </th> 
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
   <td colname="2"> L’utilisateur ou TVSDK a sélectionné un nouveau taux de lecture, tel qu’une lecture en amont rapide, en arrière ou à la reprise à une vitesse normale. </td> 
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
   <td colname="2"> L’état du lecteur multimédia a changé. Votre application doit gérer les erreurs dans ce rappel de . </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">ProfileEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/ProfileEvent.html#PROFILE_CHANGED" format="html" scope="external"> _CHANGED</a> </td> 
   <td colname="2">Le  actuel du lecteur multimédia a changé. Utilisez la propriété <span class="codeph"> ProfileEvent.</span> pour obtenir le nouvel  en cours de lecture. Utilisez la propriété <span class="codeph"> time</span> pour obtenir l’heure à laquelle ce s’est produit. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>MediaplayerItem</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> MediaPlayerItem.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#ITEM_CREATED" format="html" scope="external"> ITEM_CREATED</a> </td> 
   <td colname="2">Un <span class="codeph"> MediaPlayerItem</span> a été créé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> MediaPlayerItem.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#ITEM_UPDATED" format="html" scope="external"> ITEM_UPDATED</a> </td> 
   <td colname="2">Le lecteur multimédia a mis à jour les médias dans l’un ou l’autre des cas suivants : 
    <ul id="ul_E4D1A1D468544C3B9F8046E9B68A956D"> 
     <li id="li_35A2A417BF924E039D9CB36CFBCDFEB6">Lorsqu’une actualisation du manifeste se produit pour un fichier actif. </li> 
     <li id="li_E7AB380C212B4011B07C3B313282681C">Lorsqu’un élément VOD ou actif comporte un sous-titrage et   de sous-titrage est d’abord découvert pour une piste de sous-titrage. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Légendes et audio</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">  MediaPlayerItem.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#CAPTION_UPDATED" format="html" scope="external"> CAPTION_UPDATED</a> </td> 
   <td colname="2">Une nouvelle piste de sous-titrage a été détectée dans le flux média et la collection <span class="codeph"> closeCaptionsTracks</span> a été mise à jour. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Manifeste et chronologie</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="0"> 
   <td colname="1">TimelineEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED" format="html" scope="external"> TIMELINE_UPDATED</a> </td> 
   <td colname="2">Le lecteur multimédia a ajouté ou supprimé des publicités, de sorte qu’il dispose d’une chronologie mise à jour. <p>Le manifeste a été actualisé pour une ressource en direct et les anciennes coupures publicitaires ont été supprimées de la chronologie ou de nouvelles opportunités publicitaires (indices) ont été découvertes. Le lecteur multimédia tente de résoudre et de placer toute nouvelle publicité dans la chronologie. </p> <p> Utilisez ce pour vérifier si la chronologie comporte des mises à jour (VOD ne change pas pendant la lecture). Vous pouvez ensuite récupérer la chronologie à l’aide de <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayer.html#timeline" format="html" scope="external"> MediaPlayer.timeline</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

