---
description: Lorsqu’un utilisateur clique sur une publicité ou un bouton associé, votre application doit répondre. TVSDK fournit des informations sur l’URL de destination du clic.
seo-description: Lorsqu’un utilisateur clique sur une publicité ou un bouton associé, votre application doit répondre. TVSDK fournit des informations sur l’URL de destination du clic.
seo-title: Répondre aux clics sur les publicités
title: Répondre aux clics sur les publicités
uuid: abc5de2f-3ab0-4e00-908c-ea8b31387d4f
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# Répondre aux clics sur les publicités {#respond-to-clicks-on-ads}

TVSDK fournit des informations vous permettant d’agir sur les publicités par clic publicitaire. Lorsque vous créez l’interface utilisateur du lecteur, vous devez décider comment répondre lorsqu’un utilisateur clique sur une publicité cliquable.

Pour TVSDK pour Android, seules les publicités linéaires peuvent être cliquées.
Lorsqu’un utilisateur clique sur une publicité ou un bouton associé, votre application doit répondre. TVSDK fournit des informations sur l’URL de destination du clic.

1. Pour configurer un écouteur de événement pour TVSDK et fournir les informations de clic publicitaire, enregistrez `AdClickedEventListener.onAdClicked`.

   Lorsqu’un utilisateur clique sur une publicité ou un bouton associé, TVSDK envoie cette notification, y compris des informations sur la destination du clic.
1. Surveillez les interactions des utilisateurs sur les annonces cliquables.
1. Lorsque l’utilisateur touche ou clique sur la publicité ou le bouton, pour avertir TVSDK, appelez `notifyClick` sur le `MediaPlayerView`.
1. Prêtez attention au événement `onAdClick(AdClickEvent event)` de TVSDK.
1. Pour récupérer l’URL de clic publicitaire et les informations connexes, utilisez les méthodes getter pour l’instance `AdClickEvent`.
1. Mettez la vidéo en pause.

   Pour plus d’informations sur la mise en pause de la vidéo, voir [Mise en pause et reprise de la lecture](../../ad-insertion/clickable-ads/android-3x-pausing-resuming-playback.md).
1. Utilisez les informations de clic publicitaire pour afficher l’URL de clic publicitaire et les informations associées. Vous pouvez, par exemple, afficher les informations de l’une des manières suivantes :

   * Dans votre application, en ouvrant l’URL de clic publicitaire dans un navigateur.

      Sur les plateformes de bureau, la zone de lecture des publicités vidéo est utilisée pour appeler des URL de clic publicitaire au moment des clics des utilisateurs.
   * Redirigez les utilisateurs vers leur navigateur Web mobile externe.

      Sur les périphériques mobiles, la zone de lecture des publicités vidéo est utilisée pour d’autres fonctions, telles que masquer et afficher les commandes, suspendre la lecture, passer en mode plein écran, etc. Sur ces périphériques, une vue distincte, telle qu’un bouton de parrainage, est utilisée pour lancer l’URL de clic publicitaire.

1. Fermez la fenêtre du navigateur dans laquelle les informations de clic publicitaire s’affichent et relancez la lecture de la vidéo.

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
