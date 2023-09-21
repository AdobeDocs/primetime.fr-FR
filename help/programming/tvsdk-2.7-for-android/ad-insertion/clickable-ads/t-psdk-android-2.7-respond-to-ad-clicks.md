---
description: Lorsqu’un utilisateur clique sur une publicité ou un bouton associé, votre application doit répondre. TVSDK fournit des informations sur l’URL de destination du clic.
title: Réponse aux clics sur les publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Réponse aux clics sur les publicités {#respond-to-clicks-on-ads}

TVSDK fournit des informations qui vous permettent d’agir sur les publicités par clic publicitaire. Lorsque vous créez l’interface utilisateur de votre lecteur, vous devez décider comment répondre lorsqu’un utilisateur clique sur une publicité cliquable.

Pour TVSDK pour Android, seules les publicités linéaires peuvent être cliquées.
Lorsqu’un utilisateur clique sur une publicité ou un bouton associé, votre application doit répondre. TVSDK fournit des informations sur l’URL de destination du clic.

1. Pour configurer un écouteur d’événement pour TVSDK et fournir les informations sur les clics publicitaires, enregistrez-vous. `AdClickedEventListener.onAdClicked`.

   Lorsqu’un utilisateur clique sur une publicité ou un bouton associé, TVSDK envoie cette notification, y compris des informations sur la destination du clic.
1. Surveillez les interactions des utilisateurs sur les annonces cliquables.
1. Lorsque l’utilisateur touche ou clique sur la publicité ou le bouton, appelez pour avertir TVSDK. `notifyClick` sur le `MediaPlayerView`.
1. Écoute de la `onAdClick(AdClickEvent event)` de TVSDK.
1. Pour récupérer l’URL de clic publicitaire et les informations connexes, utilisez les méthodes getter pour la variable `AdClickEvent` instance.
1. Mettez la vidéo en pause.

   Pour plus d’informations sur la mise en pause de la vidéo, voir pause-reprise-lecture .
1. Utilisez les informations sur les clics publicitaires pour afficher l’URL des clics publicitaires et les informations associées.

       Vous pouvez, par exemple, afficher les informations de l’une des manières suivantes :
   
   * Dans votre application, en ouvrant l’URL du clic publicitaire dans un navigateur.

     Sur les plateformes de bureau, la zone de lecture des publicités vidéo est utilisée pour appeler les URL de clic publicitaire lors des clics de l’utilisateur.
   * Redirigez les utilisateurs vers leur navigateur Web mobile externe.

     Sur les appareils mobiles, la zone de lecture des publicités vidéo est utilisée pour d’autres fonctions, telles que le masquage et l’affichage des commandes, la mise en pause de la lecture, le passage en plein écran, etc. Sur ces périphériques, une vue distincte, telle qu’un bouton de parrainage, est utilisée pour lancer l’URL de clic publicitaire.

1. Fermez la fenêtre du navigateur dans laquelle les informations de clic publicitaire s’affichent et relancez la lecture de la vidéo.

<!--<a id="example_2D93228E510D438C8AB5559897817A47"></a>-->

Par exemple :

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
