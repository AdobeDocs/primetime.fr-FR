---
description: Le lecteur peut écouter une série de événements qui indiquent l’état du lecteur.
seo-description: Le lecteur peut écouter une série de événements qui indiquent l’état du lecteur.
seo-title: Configuration des notifications
title: Configuration des notifications
uuid: b178b2eb-da40-456b-997a-46ae18d635fa
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# Configurer des notifications {#set-up-notifications}

Le lecteur peut écouter une série de événements qui indiquent l’état du lecteur.

En supposant que `PTMediaPlayer` soit une propriété du lecteur client, `self.player` dans l&#39;exemple suivant représente l&#39;instance `PTMediaPlayer`. L’exemple suivant implémente la méthode `addObservers` qui s’affiche dans les instructions de configuration de PTMediaPlayer et inclut la plupart des notifications :

```
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerStatusChange:)  
      name:PTMediaPlayerStatusNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
      name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerTimeChange:)  
      name:PTMediaPlayerTimeChangeNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerItemPlayStarted:)  
      name:PTMediaPlayerPlayStartedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerItemPlayCompleted:)  
      name:PTMediaPlayerPlayCompletedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerItemTimelineChanged:)  
      name:PTMediaPlayerTimelineChangedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
      name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdBreakStarted:)  
      name:PTMediaPlayerAdBreakStartedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdBreakCompleted:)  
      name:PTMediaPlayerAdBreakCompletedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdPlayStarted:)  
      name:PTMediaPlayerAdStartedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdPlayProgress:)  
      name:PTMediaPlayerAdProgressNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdPlayCompleted:)  
      name:PTMediaPlayerAdCompletedNotification object:self.player]; 
```

## Notifications iOS {#section_65D9B2DBF5574313BD3218AB02242BBB}

`ThePTMediaPlayerNotifications` liste les notifications que TVSDK envoie à votre lecteur.

<table frame="all" colsep="1" rowsep="1" id="table_ios_notifications"> 
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <b>Notification</b> </td> 
   <td colname="2"> <b>Signification</b> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdBreakCompletedNotification  </span> </td> 
   <td colname="2"> Une coupure publicitaire s'est terminée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdBreakStartedNotification  </span> </td> 
   <td colname="2"> Une coupure publicitaire a commencé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdClickNotification  </span> </td> 
   <td colname="2"> Un utilisateur a cliqué sur une bannière publicitaire. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdCompletedNotification  </span> </td> 
   <td colname="2"> Une publicité individuelle s'est terminée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdProgressNotification  </span> </td> 
   <td colname="2"> Une publicité a progressé ; distribué constamment pendant la lecture d’une publicité. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdStartedNotification  </span> </td> 
   <td colname="2"> Une publicité individuelle a démarré. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTBackgroundManifestErrorNotification  </span> </td> 
   <td colname="2"> Échec du téléchargement du manifeste en arrière-plan. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerBufferingCompletedNotification  </span> </td> 
   <td colname="2"> La mise en mémoire tampon est terminée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerBufferingStartedNotification  </span> </td> 
   <td colname="2"> Le lecteur multimédia entre dans un état de mise en mémoire tampon. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTAudioTrackChangeCompleted  </span> </td> 
   <td colname="2"> Une modification de la piste audio du média en cours de lecture est terminée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTAudioTrackChangeStarted  </span> </td> 
   <td colname="2"> Une modification de la piste audio du média en cours de lecture est initiée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerItemChangedNotification  </span> </td> 
   <td colname="2"> Un élément <span class="codeph"> PTMediaPlayerItem </span> différent de <span class="codeph"> PTMediaPlayer </span> a été défini. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerItemDRMMetadataChanged  </span> </td> 
   <td colname="2"> Les métadonnées DRM ont été modifiées. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerMediaSelectionOptionsAvailableNotification  </span> </td> 
   <td colname="2"> Il existe de nouveaux sous-titres et d'autres pistes audio ( <span class="codeph"> PTMediaSelectionOption </span>). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerNewNotificationEntryAddedNotification  </span> </td> 
   <td colname="2"> Un nouvel élément <span class="codeph"> PTNotification </span> a été ajouté à l'élément <span class="codeph"> PTNotificationHistoryItem </span> actuel <span class="codeph"> PTMediaPlayerItem </span>, c'est-à-dire lorsqu'un événement de notification est ajouté à l'historique des notifications. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerPlayCompletedNotification  </span> </td> 
   <td colname="2"> Fin de la lecture du média. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerSeekCompletedNotification  </span> </td> 
   <td colname="2"> La recherche est terminée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerSeekErrorNotification  </span> </td> 
   <td colname="2"> L'opération de recherche en cours a échoué. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerSeekStartedNotification  </span> </td> 
   <td colname="2"> La recherche commence. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerPlayStartedNotification  </span> </td> 
   <td colname="2"> La lecture a commencé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerStatusNotification  </span> </td> 
   <td colname="2"> L’état du lecteur a changé. Les valeurs d’état possibles sont les suivantes : 
    <ul id="ul_DDBE8CAD5D5A46D2AAA6B98F0754A881"> 
     <li id="li_48F9AD580BCB4BB8A5C2DFED0DF9970F"> <p> <span class="codeph"> PTMediaPlayerStatusCreated  </span> </p> </li> 
     <li id="li_EDFB0765CF14422A95C9119DA3394163"> <p> <span class="codeph"> PTMediaPlayerStatusInitializing  </span> </p> </li> 
     <li id="li_06E1576D50C646C19E88F0F14912F2C0"> <p> <span class="codeph"> PTMediaPlayerStatusInitialized  </span> </p> </li> 
     <li id="li_E8B7157B5B234DFFABC2E5BEC241AB84"> <p> <span class="codeph"> PTMediaPlayerStatusReady  </span> </p> </li> 
     <li id="li_FF2E66B390154EAA8791B4D874CC62E1"> <p> <span class="codeph"> PTMediaPlayerStatusPlaying  </span> </p> </li> 
     <li id="li_6F3306832B7642E4BEE84068383AFAF3"> <p> <span class="codeph"> PTMediaPlayerStatusPaused  </span> </p> </li> 
     <li id="li_AE579AB888954F89A7F1115CAC0655E6"> <p> <span class="codeph"> PTMediaPlayerStatusArrêté  </span> </p> </li> 
     <li id="li_A4CEB39374E84B4AA4F7202E67B9BE43"> <p> <span class="codeph"> PTMediaPlayerStatusCompleted  </span> </p> </li> 
     <li id="li_C50EB9C459264641A9FF70EF901D7474"> <p> <span class="codeph"> PTMediaPlayerStatusError  </span> </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerTimeChangeNotification  </span> </td> 
   <td colname="2"> L’heure actuelle de lecture a changé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerTimelineChangedNotification  </span> </td> 
   <td colname="2"> La chronologie actuelle du lecteur a changé. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" colsep="1" rowsep="1"> <span class="codeph"> PTTimedMetadataChangedNotification  </span> </td> 
   <td colname="2"> TVSDK a rencontré la première occurrence d’une balise abonnée. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTTimedMetadataChangedInBackgroundNotification  </span> </td> 
   <td colname="2"> <p>Une balise abonnée est identifiée dans le manifeste d’arrière-plan et une nouvelle instance <span class="codeph"> PTTimedMetadata </span> est préparée à partir de celle-ci. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Exemples de gestionnaires pour les notifications {#section_D729C2403A234DD09596829D26882ADC}

Les extraits de code suivants illustrent certaines des façons d’utiliser les notifications.

Récupérez l&#39;instance `PTAdBreak` à l&#39;aide de `PTMediaPlayerAdBreakKey` :

```
 - (void) onMediaPlayerAdBreakStarted:(NSNotification *) notification { 
   // Fetch the PTAdBreak instance using PTMediaPlayerAdBreakKey 
   PTAdBreak *adBreak = [notification.userInfo objectForKey:PTMediaPlayerAdBreakKey]; 
   ... 
   ... 
} 
```

Définissez `subtitlesOptions` et `audioOptions` :

```
 - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification \*) notification { 
   //SubtitlesOptions and audioOptions are set and accessible now. 
   NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions;  
   NSArray* audioOp tions = self.player.currentItem.audioOptions; 
   ... 
   ... 
} 
```

Récupérez l&#39;instance `PTAd` à l&#39;aide de `PTMediaPlayerAdKey` :

```
 - (void) onMediaPlayerAdPlayStarted:(NSNotification \*)  notification { 
   // Fetch the PTAdinstance using PTMediaPlayerAdKey 
   PTAd *ad = [notification.userInfo objectForKey:PTMediaPlayerAdKey]; 
   ... 
   ... 
} 
```
