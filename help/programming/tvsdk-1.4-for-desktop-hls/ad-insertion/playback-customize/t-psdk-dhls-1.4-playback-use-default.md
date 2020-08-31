---
description: Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.
seo-description: Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.
seo-title: Utiliser le comportement de lecture par défaut
title: Utiliser le comportement de lecture par défaut
uuid: 7139384c-167a-4cab-816a-c02fb723a5cb
translation-type: tm+mt
source-git-commit: 1985694f99c548284aad6e6b4e070bece230bdf4
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---


# Utiliser le comportement de lecture par défaut{#use-the-default-playback-behavior}

Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.

Pour utiliser des comportements par défaut :

* Si vous implémentez votre propre `ContentFactory` classe, renvoyez une nouvelle instance de `DefaultAdPolicySelector` dans votre implémentation de `doRetrieveAdPolicySelector`.

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

* Si vous n’avez pas d’implémentation personnalisée pour la `ContentFactory` classe, TVSDK utilise `DefaultAdPolicySelector`.