---
description: 'null'
seo-description: 'null'
seo-title: Chargement sécurisé des publicités via HTTPS
title: Chargement sécurisé des publicités via HTTPS
uuid: 18be77cc-c59b-4982-b8c1-e4451495edd2
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Chargement sécurisé des publicités via HTTPS {#secure-ad-loading-over-https}

Adobe Primetime permet de demander un premier appel au serveur d’annonces Primetime et aux appels liés au CRS via HTTPS.

La fonction n’est pas activée par défaut. Utilisez ce qui suit pour activer le chargement sécurisé des publicités.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```
