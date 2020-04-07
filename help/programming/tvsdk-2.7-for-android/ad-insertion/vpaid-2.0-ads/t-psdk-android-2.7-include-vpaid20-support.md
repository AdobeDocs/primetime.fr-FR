---
description: Pour ajouter la prise en charge de VPAID 2.0, ajoutez un publicitaire personnalisé et des écouteurs appropriés.
seo-description: Pour ajouter la prise en charge de VPAID 2.0, ajoutez un publicitaire personnalisé et des écouteurs appropriés.
seo-title: Mise en oeuvre de l’intégration VPAID 2.0
title: Mise en oeuvre de l’intégration VPAID 2.0
uuid: fa5b9cdd-e684-4656-91b7-50781dc59e23
translation-type: tm+mt
source-git-commit: 25f97c8d296f71deddc8f9d12b97007ddf73f603

---


# Mise en oeuvre de l’intégration VPAID 2.0 {#implement-vpaid-integration}

Pour ajouter la prise en charge de VPAID 2.0, ajoutez un publicitaire personnalisé et des écouteurs appropriés.

Pour ajouter la prise en charge de VPAID 2.0 :

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

1. Créez des écouteurs et traitez le  décrit dans les -écouteurs de .

   >[!IMPORTANT]
   >
   >Dans un flux de travail VPAID 2.0, pour les publicitaires personnalisés, il est très important de conserver votre `CustomAdView` instance dans les  `AdBreak` ( `AD_BREAK_START`) et les `AdBreak` fins ( `AD_BREAK_COMPLETE`), du moment où vous créez le publicitaire personnalisé au moment où vous le supprimez. En d’autres termes, ne créez pas d’ publicitaire personnalisé pour chaque de coupure publicitaire et supprimez-le à chaque coupure publicitaire terminée.
   >
   >
   >En outre, vous ne devez créer vos  publicitaires personnalisées que lorsque votre lecteur est à l’état PRÉPARÉ,
   >
   >
   >Ne supprimez les  publicitaires personnalisées que lors de l’appel de la réinitialisation. Par exemple :
   >
   >
   ```
   >// on reset 
   >if (_mediaPlayer != null) { 
   >       _mediaPlayer.disposeCustomAdView(); 
   >       ... 
   >} 
   >```
   >
   >Enfin, avant de disposer de vos  publicitaires personnalisées, vous devez les supprimer du `FrameLayout`. Par exemple :
   >
   >
   ```
   >if (_playerFrame != null) 
   >       _playerFrame.removeAllViews(); 
   >```
