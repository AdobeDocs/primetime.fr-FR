---
description: 'null'
seo-description: 'null'
seo-title: Chargement sécurisé des publicités via HTTPS
title: Chargement sécurisé des publicités via HTTPS
uuid: 10657f59-cfbf-4c75-9249-fc154952bc51
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Chargement sécurisé des publicités via HTTPS{#secure-ad-loading-over-https}

Adobe Primetime peut demander des serveurs d’annonces tiers via https, même si le lecteur est hébergé sur http. Seuls les appels de serveurs publicitaires sont mis à niveau vers https que le client recherche pendant la phase de résolution de publicité Auditude.

>[!NOTE]
>
>Cette fonctionnalité n’est pas prise en charge pour Flash.

Utilisez ce qui suit pour activer le chargement sécurisé des publicités. Elle n’est pas activée par défaut.

```
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
auditudeSettings.forceHttpsConfiguration.adServerCalls = true;
```
