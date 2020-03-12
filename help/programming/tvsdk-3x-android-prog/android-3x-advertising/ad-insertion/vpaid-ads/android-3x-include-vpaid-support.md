---
description: Pour ajouter la prise en charge de VPAID 2.0, ajoutez un publicitaire personnalisé et des écouteurs appropriés.
seo-description: Pour ajouter la prise en charge de VPAID 2.0, ajoutez un publicitaire personnalisé et des écouteurs appropriés.
seo-title: Mise en oeuvre de l’intégration VPAID 2.0
title: Mise en oeuvre de l’intégration VPAID 2.0
uuid: d512fb5b-001c-4a7a-a553-d5962002bb30
translation-type: tm+mt
source-git-commit: 1034a0520590777cc0930d2f732741202bc3bc04

---


# Mise en oeuvre de l’intégration VPAID 2.0 {#implement-vpaid-integration}

Pour ajouter la prise en charge de VPAID 2.0, ajoutez un publicitaire personnalisé et des écouteurs appropriés.

1. Ajouter le publicitaire personnalisé  à l’interface du lecteur lorsque le lecteur est à l’état PRÉPARÉ.

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

1. Créez des écouteurs et traitez le  décrit dans la section [](../../../../tvsdk-3x-android-prog/android-3x-events-notifications/events-summary/android-3x-events-summary.md).

   >[!IMPORTANT]
   >
   >Dans un flux de travail VPAID 2.0, pour les publicitaires personnalisés, il est très important de conserver votre `CustomAdView` instance dans les  `AdBreak` ( `AD_BREAK_START`) et les `AdBreak` fins ( `AD_BREAK_COMPLETE`), du moment où vous créez le publicitaire personnalisé au moment où vous le supprimez. En d’autres termes, ne créez pas d’ publicitaire personnalisé pour chaque de coupure publicitaire et supprimez-le à chaque coupure publicitaire terminée.
   >
   >
   >En outre, vous ne devez créer vos  publicitaires personnalisées que lorsque votre lecteur est à l’état PRÉPARÉ,
   >
   >
   >Ne supprimez les  publicitaires personnalisées que lors de l’appel de la réinitialisation. Par exemple:    >
   >
   >
   ```>
   >// on reset 
   >if (_mediaPlayer != null) { 
   >       _mediaPlayer.disposeCustomAdView(); 
   >       ... 
   >} 
   >
   >```

   Enfin, avant de disposer de vos  publicitaires personnalisées, vous devez les supprimer du `FrameLayout`. Par exemple :
   >```
   >if (_playerFrame != null) 
      _playerFrame.removeAllViews(); 
   ```
