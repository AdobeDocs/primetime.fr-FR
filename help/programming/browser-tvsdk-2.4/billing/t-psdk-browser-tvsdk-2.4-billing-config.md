---
description: Si vous utilisez la configuration par défaut, il n'y a rien d'autre à faire pour activer ou configurer la facturation. Si vous avez obtenu différents paramètres de configuration de votre représentant d'activation d'Adobe, utilisez la classe BillingMetricsConfiguration pour configurer ces paramètres avant d'initialiser le lecteur de médias.
title: Configuration des mesures de facturation
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---


# Configurer les mesures de facturation{#configure-billing-metrics}

Si vous utilisez la configuration par défaut, il n&#39;y a rien d&#39;autre à faire pour activer ou configurer la facturation. Si vous avez obtenu différents paramètres de configuration de votre représentant d&#39;activation d&#39;Adobe, utilisez la classe BillingMetricsConfiguration pour configurer ces paramètres avant d&#39;initialiser le lecteur de médias.

La plupart des clients doivent utiliser la configuration par défaut.

>[!IMPORTANT]
>
>La configuration que vous définissez reste en vigueur pendant toute la durée de vie du lecteur multimédia. Une fois que vous avez initialisé le lecteur multimédia, vous ne pouvez plus modifier la configuration.

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

   où `_player` est une instance de `AdobePSDK.MediaPlayer` et `_resource` une instance de `AdobePSDK.MediaResource`.

