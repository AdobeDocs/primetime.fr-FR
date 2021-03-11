---
description: Pour ajouter la prise en charge de VPAID 2.0, ajoutez une vue publicitaire personnalisée et des écouteurs appropriés.
title: Mise en oeuvre de l’intégration VPAID 2.0
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '50'
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

