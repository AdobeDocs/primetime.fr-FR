---
description: Pour ajouter la prise en charge de VPAID 2.0, ajoutez une vue de publicité personnalisée et les écouteurs appropriés.
title: Mise en oeuvre de l’intégration VPAID 2.0
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Mise en oeuvre de l’intégration VPAID 2.0 {#implement-vpaid-integration}

Pour ajouter la prise en charge de VPAID 2.0, ajoutez une vue de publicité personnalisée et les écouteurs appropriés.

1. Ajoutez la vue de publicité personnalisée à l’interface du lecteur lorsque celui-ci est à l’état PRÉPARÉ .

   ```java
   ... 
   private FrameLayout _playerFrame; 
       ... 
       case PREPARED: 
           ... 
           addCustomView(); 
   ... 
   private void addCustomView() { 
       ... 
       WebView view = (WebView)_mediaPlayer.getCustomAdView(); 
       ... 
       _playerFrame.addView(view);
   ```

1. Créez des écouteurs et traitez les événements décrits dans la section [Événements](../../../../tvsdk-3x-android-prog/android-3x-events-notifications/events-summary/android-3x-events-summary.md).

   >[!IMPORTANT]
   >
   >Dans un workflow VPAID 2.0, il est très important de conserver votre `CustomAdView` instance sur `AdBreak` starts (événement) `AD_BREAK_START`) et `AdBreak` completes (event `AD_BREAK_COMPLETE`), à partir du moment où vous créez l’affichage d’annonce personnalisé jusqu’au moment où vous en supprimez. En d’autres termes, ne créez pas de vue de publicité personnalisée à chaque démarrage de coupure publicitaire et n’en supprimez pas à chaque coupure publicitaire.
   >
   >
   >En outre, vous ne devez créer votre vue de publicité personnalisée que lorsque votre lecteur est à l’état PRÉPARÉ,
   >
   >
   >Supprimez uniquement la vue de publicité personnalisée lorsque la réinitialisation est appelée. Par exemple :
   >
   >```
   >// on reset 
   >if (_mediaPlayer != null) { 
   >       _mediaPlayer.disposeCustomAdView(); 
   >       ... 
   >} 
   >
   >```
   >
   >Enfin, avant de disposer de votre vue d’annonce personnalisée, vous devez la supprimer de la `FrameLayout`. Par exemple :
   >
   >```
   >if (_playerFrame != null) 
   >       _playerFrame.removeAllViews(); 
   >```
