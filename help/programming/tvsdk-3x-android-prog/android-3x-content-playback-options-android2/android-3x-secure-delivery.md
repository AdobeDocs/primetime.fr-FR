---
description: TVSDK introduit la diffusion sécurisée sur HTTPS.
seo-description: TVSDK introduit la diffusion sécurisée sur HTTPS.
seo-title: Diffusion sécurisée via HTTPS
title: Diffusion sécurisée via HTTPS
translation-type: tm+mt
source-git-commit: 4a2271fc481b37bb0a437091de6efe98fcb348d9

---


# Diffusion sécurisée via HTTPS {#secure-delivery-https}

Adobe Primetime TVSDK prend en charge la diffusion HTTPS pour tous les appels provenant de TVSDK, notamment :

* Appels Auditude Ad Server
* Demandes CRS
* Appels de licence DRM
* Chaînes vidéo Analytics
* Pings de facturation

Pour utiliser cette fonctionnalité, assurez-vous que les serveurs configurés pour répondre aux demandes ci-dessus prennent en charge HTTPS.

Ce nouveau comportement n’est pas activé par défaut. Utilisez ce qui suit pour activer la diffusion sécurisée avant d’appeler à `MediaPlayer.replaceCurrentResource()`

```java
MediaPlayerItemConfig config = new MediaPlayerItemConfig(context);
NetworkConfiguration netConfig  = new NetworkConfiguration();
netConfig.setForceHTTPS(true);
config.setNetworkConfiguration(netConfig);
```
