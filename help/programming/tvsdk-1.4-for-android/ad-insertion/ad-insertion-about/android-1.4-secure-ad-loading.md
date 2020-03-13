---
description: 'null'
seo-description: 'null'
seo-title: Chargement sécurisé des publicités sur HTTPS
title: Chargement sécurisé des publicités sur HTTPS
uuid: 0d680fef-a372-4157-a89b-d9f10003c768
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Chargement sécurisé des publicités sur HTTPS{#secure-ad-loading-over-https}

Adobe Primetime propose une option pour demander un premier appel au serveur d’annonces Primetime et aux appels CRS associés via HTTPS.

La fonction n’est pas activée par défaut. Utilisez ce qui suit pour activer le chargement sécurisé des publicités.

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```

