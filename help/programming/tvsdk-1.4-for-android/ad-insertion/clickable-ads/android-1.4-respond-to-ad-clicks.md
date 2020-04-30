---
description: Lorsqu’un utilisateur clique sur une publicité ou un bouton associé, votre application doit répondre. TVSDK fournit des informations sur l’URL de destination du clic.
seo-description: Lorsqu’un utilisateur clique sur une publicité ou un bouton associé, votre application doit répondre. TVSDK fournit des informations sur l’URL de destination du clic.
seo-title: Répondre aux clics sur les publicités
title: Répondre aux clics sur les publicités
uuid: 31852f01-c900-48e3-ae23-7fb131c22594
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Répondre aux clics sur les publicités{#respond-to-clicks-on-ads}

Lorsqu’un utilisateur clique sur une publicité ou un bouton associé, votre application doit répondre. TVSDK fournit des informations sur l’URL de destination du clic.

1. Pour configurer un écouteur de événement pour TVSDK et fournir les informations de clic publicitaire, enregistrez un `AdClickedEventListener.onAdClicked`message.

   Lorsqu’un utilisateur clique sur une publicité ou un bouton associé, TVSDK envoie cette notification, y compris des informations sur la destination du clic.
1. Surveillez les interactions des utilisateurs sur les annonces cliquables.
1. Lorsque l’utilisateur touche ou clique sur la publicité ou le bouton, pour avertir TVSDK, appelez `notifyClick` le `MediaPlayerView`.
1. Prêtez attention au `onAdClick(AdClickEvent event)` événement de TVSDK.
1. Pour récupérer l’URL de clic publicitaire et les informations connexes, utilisez les méthodes getter pour l’ `AdClickEvent` instance.
1. Mettez la vidéo en pause.

   Pour plus d’informations sur la suspension de la vidéo, voir [Pause et reprise de la lecture.](../../ad-insertion/clickable-ads/android-1.4-pausing-resuming-playback.md).
1. Utilisez les informations de clic publicitaire pour afficher l’URL de clic publicitaire et les informations associées.

       Vous pouvez, par exemple, afficher les informations de l’une des manières suivantes :
   
   * Dans votre application en ouvrant l’URL de clic publicitaire dans un navigateur.

      Sur les plateformes de bureau, la zone de lecture des publicités vidéo est utilisée pour appeler des URL de clic publicitaire au moment des clics des utilisateurs.
   * Redirigez les utilisateurs vers leur navigateur Web mobile externe.

      Sur les périphériques mobiles, la zone de lecture des publicités vidéo est utilisée pour d’autres fonctions, telles que masquer et afficher les commandes, suspendre la lecture, passer en mode plein écran, etc. Sur ces périphériques, une vue distincte, telle qu’un bouton de parrainage, est utilisée pour lancer l’URL de clic publicitaire.

1. Fermez la fenêtre du navigateur dans laquelle les informations de clic publicitaire s’affichent et relancez la lecture de la vidéo.

<!--<a id="example_2D93228E510D438C8AB5559897817A47"></a>-->

Par exemple :

```java
private AdStartedEventListener adStartedEventListener = new AdStartedEventListener() { 
    @Override 
    public void onAdStarted(AdPlaybackEvent adPlaybackEvent) { 
        Ad ad = adPlaybackEvent.getAd(); 
        if (ad == null) { 
            return; 
        } 
 
        _pubOverlay.startAd(adPlaybackEvent.getAdBreak(), ad); 
 
        if (areClickableAdsEnabled() && ad.isClickable()) { 
            _isClickableAdPlaying = true; 
            _playerClickableAdFragment.show(); 
        } 
 
    } 
}; 
 
private AdCompletedEventListener adCompletedEventListener = new AdCompletedEventListener() { 
    @Override 
    public void onAdCompleted(AdPlaybackEvent adPlaybackEvent) { 
        Ad ad = adPlaybackEvent.getAd(); 
        _pubOverlay.stopAd(adPlaybackEvent.getAdBreak(), ad); 
 
        _isClickableAdPlaying = false; 
        if (ad.isClickable()) { 
            _playerClickableAdFragment.hide(); 
        } 
    } 
}; 
 
private AdClickedEventListener adClickedEventListener = new AdClickedEventListener() { 
    @Override 
    public void onAdClicked(AdClickEvent adClickEvent) { 
        AdClick adClick = adClickEvent.getAdClick(); 
        Ad ad = adClickEvent.getAd(); 
 
        String url = adClick.getUrl(); 
        if (url == null || url.trim().equals("")) { 
        } else { 
            Uri uri = Uri.parse(url); 
            Intent intent = new Intent(ACTION_VIEW, uri); 
            try { 
                startActivity(intent); 
            } catch (Exception e) { 
            } 
        } 
 
    } 
}; 
```

