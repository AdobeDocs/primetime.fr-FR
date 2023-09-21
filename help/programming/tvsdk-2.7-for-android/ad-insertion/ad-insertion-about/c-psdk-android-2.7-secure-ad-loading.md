---
title: Chargement sécurisé des publicités via HTTPS
description: Chargement sécurisé des publicités via HTTPS
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Chargement sécurisé des publicités via HTTPS {#secure-ad-loading-over-https}

Adobe Primetime permet de demander le premier appel au serveur de publicités Primetime et aux appels CRS via HTTPS.

La fonction n’est pas activée par défaut. Utilisez ce qui suit pour activer le chargement sécurisé des publicités.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```
