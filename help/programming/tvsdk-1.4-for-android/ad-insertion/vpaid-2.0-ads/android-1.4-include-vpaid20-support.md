---
description: Pour ajouter la prise en charge de VPAID 2.0, ajoutez un publicitaire personnalisé et des écouteurs appropriés.
seo-description: Pour ajouter la prise en charge de VPAID 2.0, ajoutez un publicitaire personnalisé et des écouteurs appropriés.
seo-title: Mise en oeuvre de l’intégration VPAID 2.0
title: Mise en oeuvre de l’intégration VPAID 2.0
uuid: 7d11ffd8-240c-4a95-94e6-ff4417c8942e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Mise en oeuvre de l’intégration VPAID 2.0{#implement-vpaid-integration}

Pour ajouter la prise en charge de VPAID 2.0, ajoutez un publicitaire personnalisé et des écouteurs appropriés.

Pour ajouter la prise en charge de VPAID 2.0 :

1. Ajouter le publicitaire personnalisé  à l’interface du lecteur.

   ```java
   _playerFrame.addView(mediaPlayer.createCustomAdView());
   ```

1. Ajouter un écouteur pour les  publicitaires personnalisées.

   ```java
   mediaplayer.addEventListener(MediaPlayer.Event.CUSTOM_AD,  
     _customAdEventListener);
   ```

