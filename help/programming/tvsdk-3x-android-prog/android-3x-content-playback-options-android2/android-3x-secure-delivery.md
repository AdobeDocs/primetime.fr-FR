---
description: TVSDK introduit la diffusion sécurisée via HTTPS.
title: Diffusion sécurisée via HTTPS
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# Diffusion sécurisée via HTTPS {#secure-delivery-https}

Adobe Primetime TVSDK prend en charge la diffusion HTTPS pour tous les appels provenant de TVSDK, qui incluent

* Appels au serveur d’annonces Auditude
* Requêtes CRS
* Appels de licence DRM
* Pings Video Analytics
* Pings de facturation

Pour utiliser cette fonctionnalité, assurez-vous que les serveurs configurés pour traiter les requêtes ci-dessus prennent en charge HTTPS.

Ce nouveau comportement n’est pas activé par défaut. Utilisez les éléments suivants pour activer une diffusion sécurisée avant d’appeler vers `MediaPlayer.replaceCurrentResource()`

```java
MediaPlayerItemConfig config = new MediaPlayerItemConfig(context);
NetworkConfiguration netConfig  = new NetworkConfiguration();
netConfig.setForceHTTPS(true);
config.setNetworkConfiguration(netConfig);
```
