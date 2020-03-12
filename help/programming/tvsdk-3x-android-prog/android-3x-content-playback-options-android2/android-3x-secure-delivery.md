---
description: TVSDK introduit des  sécurisées sur HTTPS.
seo-description: TVSDK introduit des  sécurisées sur HTTPS.
seo-title: ' sécurisé via HTTPS'
title: ' sécurisé via HTTPS'
translation-type: tm+mt
source-git-commit: 4a2271fc481b37bb0a437091de6efe98fcb348d9

---


#  sécurisé via HTTPS {#secure-delivery-https}

Adobe Primetime TVSDK prend en charge les  HTTPS pour tous les appels en provenance de TVSDK, notamment

* Appels Auditude Ad Server
* Demandes CRS
* Appels de licence DRM
* Anneaux d’analyse vidéo
* Pings de facturation

Pour utiliser cette fonctionnalité, assurez-vous que les serveurs configurés pour servir les requêtes ci-dessus prennent en charge HTTPS.

Ce nouveau comportement n’est pas activé par défaut. Utilisez ce qui suit pour activer la  sécurisée avant d’appeler vers `MediaPlayer.replaceCurrentResource()`

```java
MediaPlayerItemConfig config = new MediaPlayerItemConfig(context);
NetworkConfiguration netConfig  = new NetworkConfiguration();
netConfig.setForceHTTPS(true);
config.setNetworkConfiguration(netConfig);
```
