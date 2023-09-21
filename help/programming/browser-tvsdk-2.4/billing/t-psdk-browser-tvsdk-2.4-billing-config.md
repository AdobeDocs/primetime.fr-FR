---
description: Si vous utilisez la configuration par défaut, vous n’avez rien d’autre à faire pour activer ou configurer la facturation. Si vous avez obtenu différents paramètres de configuration de votre représentant d’activation Adobe, utilisez la classe BillingMetricsConfiguration pour configurer ces paramètres avant d’initialiser le lecteur multimédia.
title: Configuration des mesures de facturation
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---

# Configuration des mesures de facturation{#configure-billing-metrics}

Si vous utilisez la configuration par défaut, vous n’avez rien d’autre à faire pour activer ou configurer la facturation. Si vous avez obtenu différents paramètres de configuration de votre représentant d’activation Adobe, utilisez la classe BillingMetricsConfiguration pour configurer ces paramètres avant d’initialiser le lecteur multimédia.

La plupart des clients doivent utiliser la configuration par défaut.

>[!IMPORTANT]
>
>La configuration que vous définissez reste en vigueur pendant la durée de vie du lecteur multimédia. Une fois que vous avez initialisé le lecteur multimédia, vous ne pouvez pas modifier la configuration.

Pour configurer les mesures de facturation :

* Saisissez l’exemple de code suivant.

  ```js
  var config = new AdobePSDK.MediaPlayerItemConfig(); 
  config.billingMetricsConfiguration.isEnabled = true; 
  config.billingMetricsConfiguration.proVODBillableDurationMinutes = 60; 
  config.billingMetricsConfiguration.stdVODBillableDurationMinutes = 30; 
  config.billingMetricsConfiguration.liveBillableDurationMinutes = 15; 
  _player.replaceCurrentResource(_resource, config);
  ```

  where `_player` est une instance de `AdobePSDK.MediaPlayer` et `_resource` est une instance de `AdobePSDK.MediaResource`.
