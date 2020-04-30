---
description: Vous pouvez personnaliser ou remplacer les comportements publicitaires.
seo-description: Vous pouvez personnaliser ou remplacer les comportements publicitaires.
seo-title: Configuration de la lecture personnalisée
title: Configuration de la lecture personnalisée
uuid: 9cbf0bcf-7932-409e-a690-e79f284eaf74
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Configuration d’une lecture personnalisée {#cset-up-customized-playback}

Vous pouvez personnaliser ou remplacer le comportement d’une publicité en enregistrant l’instance de stratégie d’annonce avec TVSDK.

Pour personnaliser les comportements publicitaires, effectuez l’une des opérations suivantes :

* Implémentez l’ `AdPolicySelector` interface et toutes ses méthodes.
Cette option est recommandée si vous devez remplacer tous les comportements publicitaires par défaut.

* Étendez la `DefaultAdPolicySelector` classe et fournissez des implémentations uniquement pour les comportements qui nécessitent une personnalisation.
Cette option est recommandée si vous ne devez remplacer que certains comportements par défaut.

Pour les deux options, effectuez les tâches suivantes :

Pour personnaliser les comportements publicitaires :

1. Implémentez l’interface AdPolicySelector et toutes ses méthodes.

1. Affectez l’instance de stratégie à utiliser par TVSDK via la fabrique de publicités.

>[!ATTENTION]
>
>Les stratégies publicitaires personnalisées enregistrées au début de >la lecture sont effacées lorsque l&#39;instance MediaPlayer est >délocalisée.Votre application doit enregistrer une instance de stratégie >sélecteur chaque fois qu&#39;une nouvelle session de lecture est créée.

Par exemple :

```
    class CustomContentFactory extends ContentFactory {
     ...
    @Override
    public AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem mediaPlayerItem) {
    return new CustomAdPolicySelector(mediaPlayerItem);
    }
     ...
    }
    TVSDK 1.4 for Android Programmer's Guide 46
    // register the custom content factory with media player
    MediaPlayerItemConfig config = new MediaPlayerItemConfig();
    config.setAdvertisingFactory(new CustomContentFactory());
    // this config will should be later passed while loading the resource
    mediaPlayer.replaceCurrentResource(resource, config);
```

1. Mettez en oeuvre vos personnalisations.