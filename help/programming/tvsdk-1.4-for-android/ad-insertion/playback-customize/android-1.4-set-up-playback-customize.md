---
description: Vous pouvez personnaliser ou remplacer les comportements de publicité.
title: Configuration de la lecture personnalisée
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Configuration de la lecture personnalisée {#cset-up-customized-playback}

Vous pouvez personnaliser ou remplacer le comportement de publicité en enregistrant l’instance de stratégie publicitaire avec TVSDK.

Pour personnaliser les comportements d’annonce, effectuez l’une des opérations suivantes :

* Mettez en oeuvre le `AdPolicySelector` et toutes ses méthodes.
Cette option est recommandée si vous devez remplacer tous les comportements de publicité par défaut.

* Étendre le `DefaultAdPolicySelector` et ne fournissent des implémentations que pour les comportements qui nécessitent une personnalisation.
Cette option est recommandée si vous ne devez remplacer que certains des comportements par défaut.

Pour les deux options, effectuez les tâches suivantes :

Pour personnaliser les comportements d’annonce :

1. Implémentez l’interface AdPolicySelector et toutes ses méthodes.

1. Affectez l’instance de stratégie à utiliser par TVSDK via la fabrique de publicités.

>[!IMPORTANT]
>
>Les stratégies de publicité personnalisées enregistrées au début de la lecture sont effacées lorsque l’instance MediaPlayer est désaffectée. Votre application doit enregistrer une instance policy >selector chaque fois qu’une nouvelle session de lecture est créée.

Par exemple :

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
