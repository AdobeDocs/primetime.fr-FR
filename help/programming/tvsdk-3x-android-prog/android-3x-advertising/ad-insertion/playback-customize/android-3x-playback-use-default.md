---
description: Vous pouvez choisir d’utiliser les comportements de publicité par défaut.
title: Utilisation du comportement de lecture par défaut
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Utilisation du comportement de lecture par défaut {#use-the-default-playback-behavior}

Vous pouvez choisir d’utiliser les comportements de publicité par défaut.

1. Pour utiliser les comportements par défaut, effectuez l’une des tâches suivantes :

   * Si vous implémentez le vôtre `AdvertisingFactory` class, return null pour `createAdPolicySelector`.

   * Si vous ne disposez pas d’une implémentation personnalisée pour la variable `AdvertisingFactory` TVSDK utilise un sélecteur de stratégie de publicité par défaut.

## Configuration de la lecture personnalisée {#set-up-customized-playback}

Vous pouvez personnaliser ou remplacer les comportements de publicité.

Avant de pouvoir personnaliser ou remplacer les comportements publicitaires, enregistrez l’instance de stratégie publicitaire avec .
Pour personnaliser les comportements d’annonce, effectuez l’une des opérations suivantes :

* Mettez en oeuvre le `AdPolicySelector` et toutes ses méthodes.

  Cette option est recommandée si vous devez remplacer **all** les comportements publicitaires par défaut.

* Étendre le `DefaultAdPolicySelector` et ne fournissent des implémentations que pour les comportements qui nécessitent une personnalisation.

  Cette option est recommandée si vous devez remplacer uniquement **some** des comportements par défaut.

Pour personnaliser les comportements d’annonce :

1. Mettez en oeuvre le `AdPolicySelector` et toutes ses méthodes.
1. Affectez l’instance de stratégie à utiliser par TVSDK via la fabrique de publicités.

   >[!NOTE]
   >
   >La classe CustomContentFactory étend ContentFactory &amp;lbrace;
   >...
   >@Override
   >public AdPolicySelector retrieveAdPolicySelector>(MediaPlayerItem mediaPlayerItem) &amp;lbrace;
   >return new CustomAdPolicySelector(mediaPlayerItem);
   >&amp;brace;
   >...
   >&amp;brace;
   >// enregistrer la fabrique de contenu personnalisée avec le lecteur multimédia
   >MediaPlayerItemConfig = new MediaPlayerItemConfig();
   >config.setAdvertisingFactory(new CustomContentFactory());
   >// cette configuration doit être transmise ultérieurement lors du chargement >de la ressource
   >mediaPlayer.replaceCurrentResource(resource, config);

1. Mettez en oeuvre vos personnalisations.
