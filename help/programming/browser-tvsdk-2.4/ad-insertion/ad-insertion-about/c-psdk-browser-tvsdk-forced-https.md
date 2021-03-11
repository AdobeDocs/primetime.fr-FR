---
title: Chargement sécurisé des publicités via HTTPS
description: Chargement sécurisé des publicités via HTTPS
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---


# Chargement sécurisé des publicités par HTTPS{#secure-ad-loading-over-https}

Adobe Primetime peut demander des serveurs d’annonces tiers sur https, même si le lecteur est hébergé sur http. Seuls les appels des serveurs d’annonces sont mis à niveau vers https recherchés par le client pendant la phase de résolution des publicités Auditude.

>[!NOTE]
>
>Cette fonctionnalité n’est pas prise en charge pour le Flash.

Utilisez ce qui suit pour activer le chargement sécurisé des publicités. Elle n’est pas activée par défaut.

```
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
auditudeSettings.forceHttpsConfiguration.adServerCalls = true;
```
