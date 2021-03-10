---
description: 'De nouvelles API ont été introduites, qui demanderont à TVSDK d’ignorer l’état de connectivité réseau lors du téléchargement des manifestes. '
title: Lecture hors ligne avec Android
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---


# Lecture hors ligne avec Android {#offline-playback-with-android}

Les API suivantes ont été introduites. Elles indiquent à TVSDK d’ignorer l’état de connectivité réseau lors du téléchargement des manifestes. L’état de connectivité réseau est généralement utilisé lors de la diffusion en flux continu du débit adaptatif (ABR), pour déterminer si une tentative de secours ou une attente de reprise du réseau doivent être effectués.

```
NetworkConfiguration::setOfflinePlayback(boolean)
boolean NetworkConfiguration::getOfflinePlayback()
```

Vous pouvez activer ce paramètre et ignorer la connectivité réseau.

Définissez `com.adobe.mediacore.system.NetworkConfiguration::setOfflinePlayback` sur true. La valeur par défaut d’une valeur booléenne est false.

```
// example of NetworkConfiguration
// wherever you currently set up MediaResource and MediaPlayerItemConfig
NetworkConfiguration networkConfig = mediaPlayerItemConfig.getNetworkConfiguration();
networkConfig.setOfflinePlayback(true);
mediaPlayerItemConfig.setNetworkConfiguration(networkConfig);
```
