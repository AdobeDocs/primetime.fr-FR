---
description: Grâce à NotificationEvent, vous pouvez effectuer le suivi des avertissements transmis à partir du moteur vidéo Adobe (AVE).
seo-description: Grâce à NotificationEvent, vous pouvez effectuer le suivi des avertissements transmis à partir du moteur vidéo Adobe (AVE).
seo-title: Suivi des avertissements AVE dans votre lecteur
title: Suivi des avertissements AVE dans votre lecteur
uuid: 236aee5e-6b1a-4298-9d3b-f33b40416c19
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Suivi des avertissements AVE dans votre lecteur{#track-ave-warnings-in-your-player}

Grâce à NotificationEvent, vous pouvez effectuer le suivi des avertissements transmis à partir du moteur vidéo Adobe (AVE).

Votre application de lecteur peut effectuer le suivi des avertissements de lecture et des erreurs générés par AVE, tels que le basculement sur incident ou le réseau en aval, qui n’arrêtent pas la lecture et ne nécessitent aucune action de la part de votre application. Bien que certaines erreurs AVE soient traitées par le SDK TVSDK, `NotificationEvent` sert de mécanisme de transmission général à la couche d’application pour les avertissements AVE. Après avoir reçu des avertissements AVE, vous pouvez choisir d’effectuer certaines actions, telles que l’arrêt proactif de la lecture, l’activation d’un plan d’urgence, la consignation des messages, etc.

Utilisez les éléments d’API suivants pour effectuer le suivi des avertissements AVE dans votre lecteur :

**NotificationCode**

```
public final class NotificationCode { 
    /** 
     * Warning message for playback status. 
     */ 
    public static const GENERAL_WARNING:int = 101100; 
}
```

**NotificationEvent**

```
/** 
 * Event dispatched by MediaPlayer when a notification is available 
 * for the current media stream being played. 
 */ 
public class NotificationEvent extends Event { 
    /** 
     * Event dispatched when a new warning has been received for the current item. 
     * 
     * The newly created Notification object can be accessed through  
     * the notification property of this event. 
     */ 
    public static const WARNING_AVAILABLE:String = "warningAvailable"; 
    /** 
     * Helper method for creating NotificationEvent events. 
     * Throws an ArgumentError if the specified ad break is null. 
     * @param notification Associated notification object. 
     * 
     * @return a valid notification event instance. 
     */ 
    public static function create( 
           type:String, notification:Notification):NotificationEvent; 
     /** 
     * Default constructor 
     * Throws an ArgumentError if the specified ad break is null. 
     * @param type           Event type. 
     * @param bubbles        Whether the event can bubble up the display list hierarchy. 
     * @param cancelable     Whether the behavior associated with the event can be prevented. 
     * @param notification   Associated notification object. 
     */ 
    public function NotificationEvent(type:String,  
                                      bubbles:Boolean=false,  
                                      cancelable:Boolean=false,  
                                      notification:Notification= null); 
     /** 
     * The notification associated with this event. 
     */ 
    public function get notification():Notification; 
    /** 
     * @inheritDoc 
     */ 
    public override function clone():Event; 
}
```

Ajouter un écouteur de  votre lecteur pour capturer les avertissements AVE.

Par exemple :

```
var _player:DefaultMediaPlayer = new DefaultMediaPlayer(context); 
_player.addEventListener(NotificationEvent.WARNING_AVAILABLE, onWarningAvailable); 
 
private function onWarningAvailable(event:NotificationEvent):void { 
    var metadata:Metadata = event.notification.metadata; 
    if (metadata != null) { 
        for each (var key:String in metadata.keySet()) { 
            var value:String = metadata.getValue(key); 
            if (!StringUtils.isEmpty(key) && !StringUtils.isEmpty(value)) { 
                _logger.warn("#onWarningAvailable metadata [{0}:{1}]", key, value); 
            } 
        } 
    } 
} 
```

<!--<a id="example_C35262605D394718B40C084B569A5052"></a>-->

Voici un exemple d’avertissements AVE qui ont été suivis à l’aide de `NotificationEvent`:

```
[WARN ] [psdkdemo::PSDKDemo] #onWarningAvailable metadata [resourceType:HLS] 
[WARN ] [psdkdemo::PSDKDemo] #onWarningAvailable metadata [resourceId:0] 
[WARN ] [psdkdemo::PSDKDemo] #onWarningAvailable metadata [runtimeCode:66] 
[WARN ] [psdkdemo::PSDKDemo] #onWarningAvailable metadata [runtimeCodeMessage:SEGMENT_SKIPPED_ON_FAILURE] 
[WARN ] [psdkdemo::PSDKDemo] #onWarningAvailable metadata [eventType:Warning] 
 
<ph>
  [WARN ] [psdkdemo::PSDKDemo] #onWarningAvailable metadata [description:url::= 
   https://xyz.corp.adobe.com/pmp/assets/abc/failover/tc.1.04/content/backup-01/ 
   low-res/main-stream4-4x3-info6.ts,periodIndex::=0, 
   sizeBytes::=0,downloadTime(ms)::=0,mediaDuration(ms)::=0] 
</ph>
```
