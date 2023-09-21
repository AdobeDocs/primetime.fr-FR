---
description: Vous pouvez activer le suivi des publicités côté client en ajoutant les paramètres pttrackingmode et pttrackingversion à votre requête d’URL de Bootstrap.
title: Activation du suivi des publicités côté client
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---


# Activation du suivi des publicités côté client {#enable-client-side-ad-tracking}

Vous pouvez activer le suivi des publicités côté client en ajoutant la variable `pttrackingmode` et `pttrackingversion` à votre requête d’URL de Bootstrap.

Lorsque le suivi des publicités côté client est activé, vous pouvez également récupérer les métadonnées de suivi des publicités à l’aide de l’URL de l’API de suivi. Pour plus d’informations, voir [Paramètres de requête](/help/primetime-ad-insertion/~old-msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md).

Pour effectuer le suivi des publicités côté client, utilisez l’URL de l’API de suivi.

1. Ajoutez les paramètres de requête suivants à l’URL de requête du serveur manifeste :

   * `pttrackingmode=simple`
   * `pttrackingversion={format version}`

Par exemple :

```URL
https://. . .?. . .&pttrackingmode=simple&pttrackingversion=v1
```
