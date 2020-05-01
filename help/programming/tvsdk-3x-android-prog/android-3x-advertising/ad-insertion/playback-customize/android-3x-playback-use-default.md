---
description: Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.
seo-description: Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.
seo-title: Utiliser le comportement de lecture par défaut
title: Utiliser le comportement de lecture par défaut
uuid: 36f76c42-4c6c-4620-9b47-ec97519a642a
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

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
>classe CustomContentFactory étend ContentFactory {
>...
>@Override
>public AdPolicySelector retrieveAdPolicySelector&quot;(MediaPlayerItem mediaPlayerItem) {
>return new CustomAdPolicySelector(mediaPlayerItem);
>}
>...
>}
>// enregistrer la fabrique de contenu personnalisée avec le lecteur multimédia
>MediaPlayerItemConfig config = new MediaPlayerItemConfig();
>config.setAdvertisingFactory(new CustomContentFactory());
>// cette configuration doit être transmise ultérieurement lors du chargement >de la ressource
>mediaPlayer.replaceCurrentResource(resource, config);

1. Mettez en oeuvre vos personnalisations.