---
description: Vous pouvez choisir d’utiliser les comportements de publicité par défaut.
title: Utilisation du comportement de lecture par défaut
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 0%

---

# Utilisation du comportement de lecture par défaut{#use-the-default-playback-behavior}

Vous pouvez choisir d’utiliser les comportements de publicité par défaut.

Pour utiliser les comportements par défaut :

* Si vous implémentez le vôtre `ContentFactory` , renvoyer une nouvelle instance de `DefaultAdPolicySelector` dans votre mise en oeuvre de `doRetrieveAdPolicySelector`.

  ```
  public class CustomContentFactory extends ContentFactory { 
  
      //... 
      // your custom code for advertising classes 
      //... 
  
      /** 
       * @inheritDoc 
       */ 
      override protected function  
        doRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector { 
          return new DefaultAdPolicySelector(item); 
      } 
  }
  ```

* Si vous ne disposez pas d’une implémentation personnalisée pour la variable `ContentFactory` classe, TVSDK utilise `DefaultAdPolicySelector`.
