---
description: 'null'
seo-description: 'null'
seo-title: Chargement sécurisé des publicités sur HTTPS
title: Chargement sécurisé des publicités sur HTTPS
uuid: 72ab94d3-ee0c-4f02-adf2-c186ae6aec26
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Chargement sécurisé des publicités sur HTTPS {#secure-ad-loading-over-https}

Adobe Primetime propose une option pour demander un premier appel au serveur d’annonces Primetime et aux appels CRS associés via HTTPS.

La fonction n’est pas activée par défaut. Utilisez ce qui suit pour activer le chargement sécurisé des publicités.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```

