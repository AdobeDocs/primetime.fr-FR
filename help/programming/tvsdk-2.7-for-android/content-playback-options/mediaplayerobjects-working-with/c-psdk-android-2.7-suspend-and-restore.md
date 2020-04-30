---
description: Suspendre et restaurer TVSDK MediaPlayer lorsqu’un écran de périphérique est désactivé et activé doit être géré par votre application.
keywords: SurfaceView;Suspend;Restore;BroadcastReceiver
seo-description: Suspendre et restaurer TVSDK MediaPlayer lorsqu’un écran de périphérique est désactivé et activé doit être géré par votre application.
seo-title: Suspension et restauration de MediaPlayer
title: Suspension et restauration de MediaPlayer
uuid: 7777af91-547c-4f7a-8818-3d46dccee7d6
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Suspension et restauration de MediaPlayer {#suspend-and-restore-mediaplayer}

Suspendre et restaurer TVSDK MediaPlayer lorsqu’un écran de périphérique est désactivé et activé doit être géré par votre application.

Vous pouvez gérer les opérations de suspension et de restauration sur `MediaPlayer` le récepteur de diffusion Android pour activer/désactiver l’écran.

TVSDK ne peut pas déterminer quand un fragment (ou une Activité) se trouve en arrière-plan ou au premier plan. En outre, l’Android `SurfaceView` n’est pas détruit lorsque l’écran du périphérique est désactivé (mais que l’Activité est en pause). Cependant, `SurfaceView` il ** est détruit lorsque le périphérique met votre application en arrière-plan. TVSDK ne peut détecter aucune de ces modifications. Elles doivent donc être gérées par votre application.

L’exemple de code suivant explique comment votre application peut gérer la suspension et la restauration `MediaPlayer` lorsque l’écran du périphérique est activé et désactivé au niveau de l’application :

```java
// Track the state of a fragment to determine if it is PAUSED or RESUMED 
private boolean isActivityPaused = false; 
 
/** 
* Register the broadcast receiver to track screen on/screen off functions triggered from 
device. 
*/ 
private BroadcastReceiver mReceiver = new BroadcastReceiver() { 
    @Override 
    public void onReceive(Context context, Intent intent) { 
 
        // Call suspend when screen is turned off and mediaPlayer is not null and 
        // mediaplayer status is not suspended/Error/Released state. 
        if (intent.getAction().equals(Intent.ACTION_SCREEN_OFF)) { 
            try { 
                if (mediaPlayer != null && 
                  lastKnownStatus != MediaPlayerStatus.ERROR && 
                  lastKnownStatus != MediaPlayerStatus.RELEASED && 
                  lastKnownStatus != MediaPlayerStatus.SUSPENDED) { 
                    PrimetimeReference.logger.i(LOG_TAG+"#screenOff:", 
                    "Suspending mediaplayer as screen is turned off and mediaPlayer 
                    status is " + lastKnownStatus.toString()); 
                    mediaPlayer.suspend(); 
                } 
                else { 
                    PrimetimeReference.logger.i(LOG_TAG+"#screenOff:", 
                      "Not suspending mediaplayer since mediaplayer status is " 
                      + lastKnownStatus.toString()); 
                } 
            } catch(MediaPlayerException e) { 
                PrimetimeReference.logger.e(LOG_TAG+"#screenOff:", 
                  "MediaPlayer Exception for suspend() call"); 
            } 
        } 
        else if (intent.getAction().equals(Intent.ACTION_SCREEN_ON)) { 
            // Call restore when the screen is turned on and mediaplayer is not in the  
            // suspended status.  This is for the screen on condition when the device  
            // does not have a lock and turning on the screen immediately brings the  
            // fragment to the foreground. 
            try { 
                if(lastKnownStatus == MediaPlayerStatus.SUSPENDED && !isActivityPaused) { 
                    PrimetimeReference.logger.i(LOG_TAG+"#screenOn:", 
                      "Restoring mediaplayer since screen is turned on and mediaPlayer status is " 
                      + lastKnownStatus.toString()); 
                    mediaPlayer.restore(); 
                } 
                else { 
                    PrimetimeReference.logger.i(LOG_TAG+"#screenOn:", 
                      "Not restoring mediaplayer since mediaPlayer status is " 
                      + lastKnownStatus.toString()); 
                } 
            } catch(MediaPlayerException e) { 
                PrimetimeReference.logger.e(LOG_TAG+"#screenOn:", 
                  "MediaPlayer Exception for restore() call"); 
            } 
        } 
    } 
}; 
 
/* 
* Activity or Fragment's onPause() overridden method 
*/ 
@Override 
public void onPause() { 
    PrimetimeReference.logger.i(LOG_TAG + "#onPause", "Player activity paused."); 
 
    // Set the fragment paused status to true when app goes in background. 
    isActivityPaused = true; 
    super.onPause(); 
} 
 
/* 
* Activity or Fragment's onResume() overridden method 
*/ 
@Override 
public void onResume() { 
    super.onResume(); 
 
    /** 
    * When the device has a lock/pin the on resume will be called only after the device 
      is unlocked. 
    * Screen on does not call the onResume() method so we need to handle restore here 
      explicitly. 
    */ 
    if(lastKnownStatus == MediaPlayerStatus.SUSPENDED && isActivityPaused) { 
        try { 
            PrimetimeReference.logger.i(LOG_TAG + "#onResume", 
              "Player restored as activity operations are resumed"); 
            mediaPlayer.restore(); 
        } 
        catch(MediaPlayerException e) { 
            PrimetimeReference.logger.i(LOG_TAG + "#onResume",  
              "Exception occured while restoring mediaPlayer"); 
        } 
    } 
    // Set the fragment paused status to false when app comes in foreground. 
    isActivityPaused = false; 
} 
```
