---
description: Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.
seo-description: Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.
seo-title: Utiliser le comportement de lecture par défaut
title: Utiliser le comportement de lecture par défaut
uuid: 20785251-eb2f-4cc0-b919-1a88c0b1c57c
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Utiliser le comportement de lecture par défaut {#use-the-default-playback-behavior}

Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.

1. Pour utiliser des comportements par défaut, effectuez l’une des  de suivantes :

   * Si vous implémentez votre propre `AdvertisingFactory` classe, renvoyez la valeur null pour `createAdPolicySelector`.

   * Si vous n’avez pas d’implémentation personnalisée pour la `AdvertisingFactory` classe, TVSDK utilise un sélecteur de stratégie d’annonce par défaut.

## Configuration de la lecture personnalisée {#set-up-customized-playback}

Vous pouvez personnaliser ou remplacer les comportements publicitaires.

Avant de personnaliser ou de remplacer les comportements publicitaires, enregistrez l’instance de stratégie publicitaire avec TVSDK.

* Implémentez l’ `AdPolicySelector` interface et toutes ses méthodes.

   Cette option est recommandée si vous devez remplacer **tous les** comportements publicitaires par défaut.

* Etendez la `DefaultAdPolicySelector` classe et fournissez des implémentations uniquement pour les comportements qui nécessitent une personnalisation.

   Cette option est recommandée si vous ne devez remplacer que **certains** comportements par défaut.

Pour personnaliser les comportements publicitaires :

1. Implémentez l’ `AdPolicySelector` interface et toutes ses méthodes.
1. Affectez l’instance de stratégie à utiliser par TVSDK via la fabrique de publicités.

   >[!NOTE]
   >
   >Les stratégies publicitaires personnalisées enregistrées au début de la lecture sont effacées lorsque l’ `MediaPlayer` instance est délocalisée. Votre application doit enregistrer une instance de sélecteur de stratégies chaque fois qu’une nouvelle session de lecture est créée.

   Par exemple :

   ```java
   class CustomContentFactory extends ContentFactory { 
       ... 
       @Override 
       public AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
           return new CustomAdPolicySelector(mediaPlayerItem); 
       } 
       ... 
   } 
   
   // register the custom content factory with media player 
   MediaPlayerItemConfig config =  new MediaPlayerItemConfig(); 
   config.setAdvertisingFactory(new CustomContentFactory()); 
   
   // this config will should be later passed while loading the resource 
   mediaPlayer.replaceCurrentResource(resource, config);
   ```

1. Mettez en oeuvre vos personnalisations.