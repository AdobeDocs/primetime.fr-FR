---
description: Vous pouvez personnaliser ou remplacer les comportements de publicité.
title: Configuration de la lecture personnalisée
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Configuration de la lecture personnalisée{#set-up-customized-playback}

Vous pouvez personnaliser ou remplacer les comportements de publicité.

Avant de pouvoir personnaliser ou remplacer les comportements publicitaires, enregistrez l’instance de stratégie publicitaire avec .
Pour personnaliser les comportements d’annonce, effectuez l’une des opérations suivantes :

* Mettez en oeuvre le `AdPolicySelector` et toutes ses méthodes.

  Cette option est recommandée si vous devez remplacer **all** les comportements publicitaires par défaut.

* Étendre le `DefaultAdPolicySelector` et ne fournissent des implémentations que pour les comportements qui nécessitent une personnalisation.

  Cette option est recommandée si vous devez remplacer uniquement **some** des comportements par défaut.

Pour les deux options, effectuez les tâches suivantes :

1. Mettez en oeuvre votre propre sélecteur de stratégie de publicité personnalisée.

   ```
   public class CustomAdPolicySelector implements AdPolicySelector { 
       // your own customization here 
   }
   ```

1. Étendez la fabrique de contenu pour utiliser le sélecteur de stratégie d’annonce personnalisée.

   ```
   public class CustomContentFactory extends DefaultContentFactory { 
       /** 
        * @inheritDoc 
        */ 
       override protected function doRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector { 
           return new CustomAdPolicySelector(item); 
       } 
   }
   ```

   ```
   psdkutils::PSDKSharedPointer<psdk::ContentFactory> factory; 
   psdkFactory->createDefaultContentFactory(&factory); 
   psdkutils::PSDKSharedPointer<psdk::AdPolicySelector> defaultAdPolicySelector; 
   factory->retrieveAdPolicySelector(item, &defaultAdPolicySelector);
   ```

1. Enregistrez la nouvelle fabrique de contenu à utiliser par TVSDK dans le workflow publicitaire.

   ```
   PSDKConfig.advertisingFactory = new CustomContentFactory();
   ```

   >[!TIP]
   >
   >Si la fabrique de contenu personnalisée a été enregistrée pour un flux spécifique via la variable `MediaPlayerItemConfig` , elle sera effacée lorsque la variable `MediaPlayer` instance est désaffectée. Votre application doit l’enregistrer chaque fois qu’une nouvelle session de lecture est créée.
