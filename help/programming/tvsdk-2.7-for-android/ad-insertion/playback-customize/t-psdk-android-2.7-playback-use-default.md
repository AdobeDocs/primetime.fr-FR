---
description: Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.
title: Utiliser le comportement de lecture par défaut
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Utiliser le comportement de lecture par défaut {#use-the-default-playback-behavior}

Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.

1. Pour utiliser des comportements par défaut, effectuez l’une des tâches suivantes :

   * Si vous implémentez votre propre classe `AdvertisingFactory`, renvoyez la valeur null pour `createAdPolicySelector`.

   * Si vous n’avez pas d’implémentation personnalisée pour la classe `AdvertisingFactory`, TVSDK utilise un sélecteur de stratégie d’annonce par défaut.

## Configurer la lecture personnalisée {#set-up-customized-playback}

Vous pouvez personnaliser ou remplacer les comportements publicitaires.

Avant de personnaliser ou de remplacer des comportements publicitaires, enregistrez l’instance de stratégie publicitaire avec TVSDK.

* Implémentez l&#39;interface `AdPolicySelector` et toutes ses méthodes.

   Cette option est recommandée si vous devez remplacer **tous** les comportements publicitaires par défaut.

* Étendez la classe `DefaultAdPolicySelector` et fournissez des implémentations uniquement pour les comportements qui nécessitent une personnalisation.

   Cette option est recommandée si vous ne devez remplacer que **certains** des comportements par défaut.

Pour personnaliser les comportements publicitaires :

1. Implémentez l&#39;interface `AdPolicySelector` et toutes ses méthodes.
1. Affectez l’instance de stratégie à utiliser par TVSDK via la fabrique de publicités.

   >[!NOTE]
   >
   >Les stratégies publicitaires personnalisées qui sont enregistrées au début de la lecture sont effacées lorsque l&#39;instance `MediaPlayer` est délocalisée. Votre application doit enregistrer une instance de sélecteur de stratégies chaque fois qu’une nouvelle session de lecture est créée.

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