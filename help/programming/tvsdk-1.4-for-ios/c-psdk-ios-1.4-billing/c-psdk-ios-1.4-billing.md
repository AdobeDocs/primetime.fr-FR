---
description: Pour tenir compte des clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte les mesures d’utilisation et les utilise pour déterminer le montant de facturation des clients.
title: Mesures de facturation
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Mesures de facturation {#billing-metrics}

Pour tenir compte des clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte les mesures d’utilisation et les utilise pour déterminer le montant de facturation des clients.

Chaque fois que le lecteur génère un événement de démarrage de flux, TVSDK commence à envoyer régulièrement des messages HTTP au système de facturation de l’Adobe. La période, appelée durée facturable, peut être différente pour le contenu VOD standard, le pro VOD (publicités mid-roll activées) et le contenu en direct. La durée par défaut de chaque type de contenu est de 30 minutes, mais votre contrat avec Adobe détermine les valeurs réelles.

Les messages contiennent les informations suivantes :

* Type de contenu (actif, linéaire ou VOD)
* URL de contenu
* Si les publicités sont activées
* Si les publicités mid-roll sont activées (VOD uniquement)
* Si le flux est protégé par DRM
* Version et plateforme TVSDK

Adobe préconfigure cette disposition, mais si vous souhaitez la modifier, contactez votre représentant d’activation d’Adobe.

Pour surveiller les statistiques envoyées par TVSDK à Adobe, obtenez l’URL auprès de votre représentant d’activation de l’Adobe et utilisez un outil de capture réseau, par exemple Charles, pour afficher les données.

## Configuration des mesures de facturation {#configure-billing-metrics}

Si vous utilisez la configuration par défaut, vous n’avez rien d’autre à faire pour activer ou configurer la facturation. Si vous avez obtenu différents paramètres de configuration de votre représentant d’activation Adobe, utilisez la classe PTBillingMetricsConfiguration pour configurer ces paramètres avant d’initialiser le lecteur multimédia.

La plupart des clients doivent utiliser la configuration par défaut.

>[!IMPORTANT]
>
>La configuration que vous définissez reste en vigueur pendant la durée de vie du lecteur multimédia. Une fois que vous avez initialisé le lecteur multimédia, vous ne pouvez pas modifier la configuration.

Pour configurer les mesures de facturation :

1. Saisissez l’exemple de code suivant.

   ```
   PTBillingMetricsConfiguration *billingConfig = [[[PTBillingMetricsConfiguration alloc] init] autorelease]; 
   billingConfig.enabled = YES; 
   billingConfig.stdVODBillableDurationMinutes = 60.0; 
   billingConfig.proVODBillableDurationMinutes = 30.0; 
   billingConfig.liveBillableDurationMinutes = 15.0; 
   
   // metadata is the PTMetadata instance set on PTMediaPlayerItem 
   [metadata setMetadata:billingConfig forKey:PTBillingMetricsConfigurationMetadataKey];
   ```

## Transmettre les mesures de facturation {#transmit-billing-metrics}

TVSDK envoie les mesures de facturation à Adobe au format XML.

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

Si vous utilisez un outil de capture réseau pour surveiller les statistiques que TVSDK transmet à Adobe, vous devriez voir des unités comme celles-ci :

```
<request> 
     <sc_xml_ver>1.0</sc_xml_ver> 
     <reportSuiteID>ptebilling</reportSuiteID> 
     <visitorID>5536C629-5EF7-4F02-8E5D-9FA136CB3CED</visitorID> 
     <pageName>com.adobe.primetime.psdksample</pageName> 
     <timestamp>2016-11-22T18:06:30+0000</timestamp> 
     <userAgent>Mozilla/5.0 (iPad; CPU OS 9_1 like Mac OS X) AppleWebKit/601.1.46 (KHTML, like Gecko) Mobile/13B143</userAgent> 
     <contextData> 
         <billingMetrics> 
                 <contentDuration>1799111</contentDuration> 
                 <contentURL>https%3A%2F%2Fdevimages.apple.com.edgekey.net%2Fstreaming%2Fexamples%2Fbipbop_16x9%2Fbipbop_16x9_variant.m3u8</contentURL> 
                 <contentType>vod</contentType> 
                 <midrollEnabled>true</midrollEnabled> 
                 <tvsdkVersion>1.0.211</tvsdkVersion> 
                 <platform>Mozilla/5.0 (iPad; CPU OS 9_1 like Mac OS X) AppleWebKit/601.1.46 (KHTML, like Gecko) Mobile/13B143</platform> 
                 <publisherID>com.adobe.primetime.psdksample</publisherID> 
                 <adsEnabled>true</adsEnabled> 
                 <type>start</type> 
         </billingMetrics> 
     </contextData> 
</request>
```

Propriétés booléennes `drmProtected`, `adsEnabled`, et `midrollEnabled` apparaissent uniquement s’ils sont vrais.
