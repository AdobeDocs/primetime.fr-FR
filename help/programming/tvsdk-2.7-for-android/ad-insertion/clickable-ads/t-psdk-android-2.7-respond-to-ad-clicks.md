---
description: Lorsqu’un utilisateur clique sur une publicité ou sur un bouton associé, votre application doit répondre. TVSDK vous fournit des informations sur l’URL de destination du clic.
seo-description: Lorsqu’un utilisateur clique sur une publicité ou sur un bouton associé, votre application doit répondre. TVSDK vous fournit des informations sur l’URL de destination du clic.
seo-title: Répondre aux clics sur les publicités
title: Répondre aux clics sur les publicités
uuid: 58efaba5-d0f6-4ddd-9628-6bc065cc95d8
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Répondre aux clics sur les publicités {#respond-to-clicks-on-ads}

TVSDK vous fournit des informations pour que vous puissiez agir sur les publicités par clics publicitaires. Lorsque vous créez l’interface utilisateur du lecteur, vous devez décider de la manière dont vous répondez lorsqu’un utilisateur clique sur une publicité cliquable.

Pour TVSDK pour Android, seules les publicités linéaires peuvent être cliquées.
Lorsqu’un utilisateur clique sur une publicité ou sur un bouton associé, votre application doit répondre. TVSDK vous fournit des informations sur l’URL de destination du clic.

1. Pour configurer un écouteur de  pour TVSDK et fournir les informations de clic publicitaire, enregistrez-vous `AdClickedEventListener.onAdClicked`.

   Lorsqu’un utilisateur clique sur une publicité ou un bouton associé, TVSDK envoie cette notification, y compris des informations sur la destination du clic.
1. Surveillez les interactions des utilisateurs sur les annonces cliquables.
1. Lorsque l’utilisateur touche ou clique sur la publicité ou le bouton, pour avertir TVSDK, appelez `notifyClick` le `MediaPlayerView`.
1. Écoutez le `onAdClick(AdClickEvent event)` de TVSDK.
1. Pour récupérer l’URL de clic publicitaire et les informations connexes, utilisez les méthodes getter pour l’ `AdClickEvent` instance.
1. Mettez la vidéo en pause.

   Pour plus d’informations sur la mise en pause de la vidéo, voir Mise en pause-reprise-lecture.
1. Utilisez les informations de clic publicitaire pour afficher l’URL de clic publicitaire et les informations associées.

       Vous pouvez, par exemple, afficher les informations de l’une des manières suivantes :
   
   * Dans votre application, en ouvrant l’URL du clic publicitaire dans un navigateur.

      Sur les plateformes de bureau, la zone de lecture des publicités vidéo est utilisée pour appeler les URL de clics publicitaires au moment des clics des utilisateurs.
   * Redirigez les utilisateurs vers leur navigateur Web mobile externe.

      Sur les périphériques mobiles, la zone de lecture des publicités vidéo est utilisée pour d’autres fonctions, telles que le masquage et l’affichage des commandes, la mise en pause de la lecture, le développement en plein écran, etc. Sur ces périphériques, un distinct, tel qu’un bouton de sponsor, est utilisé pour lancer l’URL de clic publicitaire.

1. Fermez la fenêtre du navigateur dans laquelle les informations de clic publicitaire sont affichées et relancez la lecture de la vidéo.

<!--<a id="example_2D93228E510D438C8AB5559897817A47"></a>-->

Par exemple :

```java
private AdStartedEventListener adStartedEventListener =  
  new AdStartedEventListener() { 
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
 
private AdCompletedEventListener adCompletedEventListener =  
  new AdCompletedEventListener() { 
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
 
private AdClickedEventListener adClickedEventListener =  
  new AdClickedEventListener() { 
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

