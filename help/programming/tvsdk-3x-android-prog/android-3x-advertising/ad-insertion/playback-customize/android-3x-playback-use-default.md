---
description: Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.
seo-description: Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.
seo-title: Utiliser le comportement de lecture par défaut
title: Utiliser le comportement de lecture par défaut
uuid: 36f76c42-4c6c-4620-9b47-ec97519a642a
translation-type: tm+mt
source-git-commit: 6da7d597503d98875735c54e9a794f8171ad408b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---


# Utiliser le comportement de lecture par défaut {#use-the-default-playback-behavior}

Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.

1. Pour utiliser des comportements par défaut, effectuez l’une des tâches suivantes :

   * Si vous implémentez votre propre `AdvertisingFactory` classe, renvoyez la valeur null pour `createAdPolicySelector`.

   * Si vous n’avez pas d’implémentation personnalisée pour la `AdvertisingFactory` classe, TVSDK utilise un sélecteur de stratégie d’annonce par défaut.

## Configuration de la lecture personnalisée {#set-up-customized-playback}

Vous pouvez personnaliser ou remplacer les comportements publicitaires.

Avant de pouvoir personnaliser ou remplacer des comportements publicitaires, enregistrez l’instance de stratégie publicitaire avec .
Pour personnaliser les comportements publicitaires, effectuez l’une des opérations suivantes :

* Implémentez l’ `AdPolicySelector` interface et toutes ses méthodes.

   Cette option est recommandée si vous devez remplacer **tous les** comportements publicitaires par défaut.

* Étendez la `DefaultAdPolicySelector` classe et fournissez des implémentations uniquement pour les comportements qui nécessitent une personnalisation.

   Cette option est recommandée si vous ne devez remplacer que **certains** comportements par défaut.

Pour personnaliser les comportements publicitaires :

1. Implémentez l’ `AdPolicySelector` interface et toutes ses méthodes.
1. Affectez l’instance de stratégie à utiliser par TVSDK via la fabrique de publicités.

   >[!NOTE]
   >
   >classe CustomContentFactory étend ContentFactory &amp;lbrace;
   >...
   >@Override
   >public AdPolicySelector retrieveAdPolicySelector&quot;(MediaPlayerItem mediaPlayerItem) &amp;lbrace;
   >return new CustomAdPolicySelector(mediaPlayerItem);
   >&amp;amp ; accolade ;
   >...
   >&amp;amp ; accolade ;
   >// enregistrer la fabrique de contenu personnalisée avec le lecteur multimédia
   >MediaPlayerItemConfig config = new MediaPlayerItemConfig();
   >config.setAdvertisingFactory(new CustomContentFactory());
   >// cette configuration doit être transmise ultérieurement lors du chargement >de la ressource
   >mediaPlayer.replaceCurrentResource(resource, config);

1. Mettez en oeuvre vos personnalisations.
