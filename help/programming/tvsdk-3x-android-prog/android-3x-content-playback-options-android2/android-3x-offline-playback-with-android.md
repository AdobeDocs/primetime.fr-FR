---
description: De nouvelles API ont été introduites, qui vont demander à TVSDK d’ignorer l’état de connectivité réseau lors du téléchargement des manifestes.
title: Lecture hors ligne avec Android
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Lecture hors ligne avec Android {#offline-playback-with-android}

Les API suivantes ont été introduites afin d’indiquer à TVSDK d’ignorer l’état de connectivité réseau lors du téléchargement des manifestes. L’état de connectivité réseau est généralement utilisé lors de la diffusion en continu à débit adaptatif (ABR), pour déterminer si une reprise doit être effectuée ou si le réseau doit attendre sa reprise.

```
NetworkConfiguration::setOfflinePlayback(boolean)
boolean NetworkConfiguration::getOfflinePlayback()
```

Vous pouvez activer ce paramètre et ignorer la connectivité réseau.

Définir `com.adobe.mediacore.system.NetworkConfiguration::setOfflinePlayback` sur true. La valeur par défaut d’une valeur booléenne est false.

```
// example of NetworkConfiguration
// wherever you currently set up MediaResource and MediaPlayerItemConfig
NetworkConfiguration networkConfig = mediaPlayerItemConfig.getNetworkConfiguration();
networkConfig.setOfflinePlayback(true);
mediaPlayerItemConfig.setNetworkConfiguration(networkConfig);
```
