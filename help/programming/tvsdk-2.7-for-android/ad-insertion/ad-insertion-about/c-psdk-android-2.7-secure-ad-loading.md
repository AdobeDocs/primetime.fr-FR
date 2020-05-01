---
description: 'null'
seo-description: 'null'
seo-title: Chargement sécurisé des publicités via HTTPS
title: Chargement sécurisé des publicités via HTTPS
uuid: 72ab94d3-ee0c-4f02-adf2-c186ae6aec26
translation-type: tm+mt
source-git-commit: ''

---


# Chargement sécurisé des publicités via HTTPS {#secure-ad-loading-over-https}

Adobe Primetime permet de demander un premier appel au serveur d’annonces Primetime et aux appels liés au CRS via HTTPS.

La fonction n’est pas activée par défaut. Utilisez ce qui suit pour activer le chargement sécurisé des publicités.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```

