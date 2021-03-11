---
title: Chargement sécurisé des publicités via HTTPS
description: Chargement sécurisé des publicités via HTTPS
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---


# Chargement sécurisé des publicités par HTTPS {#secure-ad-loading-over-https}

Adobe Primetime offre une option permettant de demander un premier appel au serveur d’annonces Primetime et aux appels liés au CRS via HTTPS.

La fonction n’est pas activée par défaut. Utilisez ce qui suit pour activer le chargement sécurisé des publicités.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```
