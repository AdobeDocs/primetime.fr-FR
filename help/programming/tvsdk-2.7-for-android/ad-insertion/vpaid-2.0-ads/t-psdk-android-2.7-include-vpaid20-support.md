---
description: Pour ajouter la prise en charge de VPAID 2.0, ajoutez une vue publicitaire personnalisée et des écouteurs appropriés.
seo-description: Pour ajouter la prise en charge de VPAID 2.0, ajoutez une vue publicitaire personnalisée et des écouteurs appropriés.
seo-title: Mise en oeuvre de l’intégration VPAID 2.0
title: Mise en oeuvre de l’intégration VPAID 2.0
uuid: fa5b9cdd-e684-4656-91b7-50781dc59e23
translation-type: tm+mt
source-git-commit: 25f97c8d296f71deddc8f9d12b97007ddf73f603

---


# Mise en oeuvre de l’intégration VPAID 2.0 {#implement-vpaid-integration}

Pour ajouter la prise en charge de VPAID 2.0, ajoutez une vue publicitaire personnalisée et des écouteurs appropriés.

Pour ajouter la prise en charge de VPAID 2.0 :

1. Ajouter la vue publicitaire personnalisée à l’interface du lecteur lorsque celui-ci est à l’état PRÉPARÉ.

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

1. Créez des écouteurs et traitez les événements décrits dans la section écouteurs de événement .

   >[!IMPORTANT]
   >
   >Dans un flux de travail VPAID 2.0, pour les vues publicitaires personnalisées, il est très important de conserver votre `CustomAdView` instance dans `AdBreak` les débuts (événement `AD_BREAK_START`) et `AdBreak` se termine (événement `AD_BREAK_COMPLETE`), du moment où vous créez la vue publicitaire personnalisée au moment où vous en disposez. En d’autres termes, ne créez pas de vue publicitaire personnalisée sur chaque début de coupure publicitaire et supprimez-la à chaque coupure publicitaire terminée.
   >
   >
   >En outre, vous ne devez créer votre vue publicitaire personnalisée que lorsque votre lecteur est à l’état PRÉPARÉ,
   >
   >
   >Ne supprimez la vue publicitaire personnalisée que lorsque la réinitialisation est appelée. Par exemple :
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
   >Enfin, avant de disposer de votre vue publicitaire personnalisée, vous devez la supprimer de la `FrameLayout`. Par exemple :
   >
   >
   ```
   >if (_playerFrame != null) 
   >       _playerFrame.removeAllViews(); 
   >```
