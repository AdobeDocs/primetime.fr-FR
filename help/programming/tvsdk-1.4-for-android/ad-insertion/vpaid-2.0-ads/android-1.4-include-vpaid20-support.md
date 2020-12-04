---
description: Pour ajouter la prise en charge de VPAID 2.0, ajoutez une vue publicitaire personnalisée et des écouteurs appropriés.
seo-description: Pour ajouter la prise en charge de VPAID 2.0, ajoutez une vue publicitaire personnalisée et des écouteurs appropriés.
seo-title: Mise en oeuvre de l’intégration VPAID 2.0
title: Mise en oeuvre de l’intégration VPAID 2.0
uuid: 7d11ffd8-240c-4a95-94e6-ff4417c8942e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---


# Mise en oeuvre de l’intégration VPAID 2.0{#implement-vpaid-integration}

Pour ajouter la prise en charge de VPAID 2.0, ajoutez une vue publicitaire personnalisée et des écouteurs appropriés.

Pour ajouter la prise en charge de VPAID 2.0 :

1. Ajoutez la vue publicitaire personnalisée à l’interface du lecteur.

   ```java
   _playerFrame.addView(mediaPlayer.createCustomAdView());
   ```

1. Ajoutez un écouteur pour les événements publicitaires personnalisés.

   ```java
   mediaplayer.addEventListener(MediaPlayer.Event.CUSTOM_AD,  
     _customAdEventListener);
   ```

