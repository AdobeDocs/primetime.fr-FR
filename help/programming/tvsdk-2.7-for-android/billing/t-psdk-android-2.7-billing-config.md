---
description: Si vous utilisez la configuration par défaut, il n'y a rien d'autre à faire pour activer ou configurer la facturation. Si vous avez obtenu différents paramètres de configuration de votre représentant d'activation d'Adobe, utilisez la classe BillingMetricsConfiguration pour configurer ces paramètres avant d'initialiser le lecteur de médias.
seo-description: Si vous utilisez la configuration par défaut, il n'y a rien d'autre à faire pour activer ou configurer la facturation. Si vous avez obtenu différents paramètres de configuration de votre représentant d'activation d'Adobe, utilisez la classe BillingMetricsConfiguration pour configurer ces paramètres avant d'initialiser le lecteur de médias.
seo-title: Configuration des mesures de facturation
title: Configuration des mesures de facturation
uuid: d8656ab2-fdd8-4fe4-8578-a6c8ecd378e2
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---


# Configurer les mesures de facturation {#configure-billing-metrics}

Si vous utilisez la configuration par défaut, il n&#39;y a rien d&#39;autre à faire pour activer ou configurer la facturation. Si vous avez obtenu différents paramètres de configuration de votre représentant d&#39;activation d&#39;Adobe, utilisez la classe BillingMetricsConfiguration pour configurer ces paramètres avant d&#39;initialiser le lecteur de médias.

>[!TIP]
>
>La plupart des clients doivent utiliser la configuration par défaut.

>[!IMPORTANT]
>
>La configuration que vous définissez reste en vigueur pendant toute la durée de vie du lecteur multimédia. Une fois que vous avez initialisé le lecteur multimédia, vous ne pouvez plus modifier la configuration.

Pour configurer les mesures de facturation :

1. Saisissez l’exemple de code suivant.

   ```java
   MediaPlayerItemConfig config = new MediaPlayerItemConfig(); 
   BillingMetricsConfiguration billingConfig = new BillingMetricsConfiguration(); 
   billingConfig.setEnabled(true); 
   billingConfig.setProVODBillableDurationMinutes(60); 
   billingConfig.setStdVODBillableDurationMinutes(30); 
   billingConfig.setLiveBillableDurationMinutes(15); 
   config.setBillingMetricsConfiguration(billingConfig); 
   mediaPlayer.replaceCurrentResource(mediaResource, config);
   ```

