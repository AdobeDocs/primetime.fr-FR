---
title: Chargement sécurisé des publicités par HTTPS
description: Chargement sécurisé des publicités par HTTPS
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---

# Chargement sécurisé des publicités par HTTPS{#secure-ad-loading-over-https}

Adobe Primetime peut demander des serveurs d’annonces tiers via https, même si le lecteur est hébergé sur http. Seuls les appels des serveurs d’annonces sont mis à niveau vers https que le client recherche pendant la phase de résolution de la publicité Auditude.

>[!NOTE]
>
>Cette fonctionnalité n’est pas prise en charge par Flash.

Utilisez ce qui suit pour activer le chargement sécurisé des publicités. Elle n’est pas activée par défaut.

```
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
auditudeSettings.forceHttpsConfiguration.adServerCalls = true;
```
