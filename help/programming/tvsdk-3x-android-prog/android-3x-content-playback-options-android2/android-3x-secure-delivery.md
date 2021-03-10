---
description: TVSDK introduit la diffusion sécurisée sur HTTPS.
title: Diffusion sécurisée via HTTPS
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---


# Sécuriser la Diffusion via HTTPS {#secure-delivery-https}

Adobe Primetime TVSDK prend en charge la diffusion HTTPS pour tous les appels provenant de TVSDK, notamment :

* Appels Auditude Ad Server
* Demandes CRS
* Appels de licence DRM
* Chaînes vidéo Analytics
* Pings de facturation

Pour utiliser cette fonctionnalité, assurez-vous que les serveurs configurés pour répondre aux demandes ci-dessus prennent en charge HTTPS.

Ce nouveau comportement n’est pas activé par défaut. Utilisez ce qui suit pour activer la diffusion sécurisée avant d&#39;appeler `MediaPlayer.replaceCurrentResource()`

```java
MediaPlayerItemConfig config = new MediaPlayerItemConfig(context);
NetworkConfiguration netConfig  = new NetworkConfiguration();
netConfig.setForceHTTPS(true);
config.setNetworkConfiguration(netConfig);
```
