---
description: Vous pouvez personnaliser ou remplacer les comportements publicitaires.
seo-description: Vous pouvez personnaliser ou remplacer les comportements publicitaires.
seo-title: Configuration de la lecture personnalisée
title: Configuration de la lecture personnalisée
uuid: 479ca1b0-6b3f-42fa-85e1-31d707da8730
translation-type: tm+mt
source-git-commit: a21a5fcc819a7bec58ad36e118d04f462ec3fd92
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---


# Configuration de la lecture personnalisée{#set-up-customized-playback}

Vous pouvez personnaliser ou remplacer les comportements publicitaires.

Avant de pouvoir personnaliser ou remplacer des comportements publicitaires, enregistrez l’instance de stratégie publicitaire avec .
Pour personnaliser les comportements publicitaires, effectuez l’une des opérations suivantes :

* Implémentez l&#39;interface `AdPolicySelector` et toutes ses méthodes.

   Cette option est recommandée si vous devez remplacer **tous** les comportements publicitaires par défaut.

* Étendez la classe `DefaultAdPolicySelector` et fournissez des implémentations uniquement pour les comportements qui nécessitent une personnalisation.

   Cette option est recommandée si vous ne devez remplacer que **certains** des comportements par défaut.

Pour les deux options, effectuez les tâches suivantes :

1. Mettez en oeuvre votre propre sélecteur de stratégies d’annonces personnalisées.

   ```
   public class CustomAdPolicySelector implements AdPolicySelector { 
       // your own customization here 
   }
   ```

1. Etendez la fabrique de contenu pour utiliser le sélecteur de stratégie d’annonce personnalisée.

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

1. Enregistrez la nouvelle fabrique de contenu à utiliser par TVSDK dans le processus publicitaire.

   ```
   PSDKConfig.advertisingFactory = new CustomContentFactory();
   ```

   >[!TIP]
   >
   >Si la fabrique de contenu personnalisée a été enregistrée pour un flux spécifique via la classe `MediaPlayerItemConfig`, elle sera effacée lorsque l&#39;instance `MediaPlayer` sera délocalisée. Votre application doit l’enregistrer chaque fois qu’une nouvelle session de lecture est créée.