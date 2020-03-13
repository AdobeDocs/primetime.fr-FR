---
description: TVSDK distribue des de lecture lorsque des opérations de lecture multimédia se produisent, comme le démarrage de la lecture d’une vidéo.
seo-description: TVSDK distribue des de lecture lorsque des opérations de lecture multimédia se produisent, comme le démarrage de la lecture d’une vidéo.
seo-title: 'de lecture '
title: 'de lecture '
uuid: 809a8e0e-f4d8-4013-b04a-49fb93d7ca8a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# de lecture{#playback-events}

TVSDK distribue des de lecture lorsque des opérations de lecture multimédia se produisent, comme le démarrage de la lecture d’une vidéo.

Pour être averti de tous les  de liés à la lecture, enregistrez une mise en oeuvre de `MediaPlayer.PlaybackEventListener`, y compris les rappels de suivants.

<table frame="all" colsep="1" rowsep="1"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry">  </th> 
   <th colname="2" class="entry"> Signification </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="col1"><b>Lecture</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onPlayComplete%28%29" format="html" scope="external"> onPlayComplete</a> </td> 
   <td colname="2"> La fin d'une source de médias a été atteinte. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onPlayStart%28%29" format="html" scope="external"> onPlayStart</a> </td> 
   <td colname="2"> La lecture d’une source multimédia a commencé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onRateSelected%28float%29" format="html" scope="external"> onRateSelected</a> (taux en virgule flottante) </td> 
   <td colname="2"> L’utilisateur ou TVSDK a sélectionné un nouveau taux de lecture, tel qu’une lecture en amont rapide, en arrière ou à la reprise à une vitesse normale. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onRatePlaying%28float%29" format="html" scope="external"> onRatePlaying</a> (taux en virgule flottante) </td> 
   <td colname="2"> Un nouveau taux de lecture est visible à l’écran. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>Média</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onPrepared%28%29" format="html" scope="external"> onPrepared</a> </td> 
   <td colname="2"> Le lecteur de médias a préparé le média avec succès. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onSizeAvailable%28long,%20long%29" format="html" scope="external"> onSizeAvailable</a> (hauteur longue, largeur longue) </td> 
   <td colname="2"> La taille du média est disponible. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>Lecteur multimédia</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onStateChanged%28com.adobe.mediacore.MediaPlayer.PlayerState,com.adobe.mediacore.MediaPlayerNotification%29" format="html" scope="external"> onStateChanged</a> (état<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlayerState.html" format="html" scope="external"> MediaPlayer.PlayerState</a> , <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html" format="html" scope="external"> notification MediaPlayerNotification</a> ) </td> 
   <td colname="2"> L’état du lecteur multimédia a changé. Votre application doit gérer les erreurs dans ce rappel. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onProfileChanged%28long,%20long%29" format="html" scope="external"> onProfileChanged</a> (long , long terme) </td> 
   <td colname="2"> Le  actuel du lecteur multimédia a changé. Utilisez la propriété <span class="codeph"></span> du pour obtenir le nouvel  en cours de lecture. Utilisez la propriété <span class="codeph"> time</span> pour obtenir l’heure à laquelle ce s’est produit. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>MediaplayerItem</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onUpdated%28%29" format="html" scope="external"> onUpdate</a> </td> 
   <td colname="2">Le lecteur multimédia a mis à jour les médias dans l’un ou l’autre des cas suivants : 
    <ul> 
     <li>Lorsqu’une actualisation du manifeste se produit pour un fichier actif.</li> 
     <li>Lorsqu’un élément VOD ou actif comporte un sous-titrage et   de sous-titrage est d’abord découvert pour une piste de sous-titrage. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>Manifeste et chronologie</b></td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimedMetadata%28com.adobe.mediacore.metadata.TimedMetadata%29" format="html" scope="external"> onTimedMetadata</a> (<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/TimedMetadata.html" format="html" scope="external"> TimedMetadata</a> timedMetadata) </td> 
   <td colname="2"> Une nouvelle métadonnée minutée est découverte dans le manifeste. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated%28%29" format="html" scope="external"> onTimelineUpdate</a> </td> 
   <td colname="2">Le lecteur multimédia a ajouté ou supprimé des publicités, de sorte qu’il dispose d’une chronologie mise à jour. <p>Le manifeste a été actualisé pour une ressource en direct et les anciennes coupures publicitaires ont été supprimées de la chronologie ou de nouvelles opportunités publicitaires (indices) ont été découvertes. Le lecteur multimédia tente de résoudre et de placer toute nouvelle publicité dans la chronologie. </p><p> Utilisez ce pour vérifier si la chronologie comporte des mises à jour (VOD ne change pas pendant la lecture). Vous pouvez ensuite récupérer la chronologie à l’aide de <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.html#getTimeline%28%29" format="html" scope="external"> MediaPlayer.getTimeline</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>
