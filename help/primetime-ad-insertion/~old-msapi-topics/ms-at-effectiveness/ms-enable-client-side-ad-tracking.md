---
description: Vous pouvez activer le suivi des publicités côté client en ajoutant les paramètres de version pttrackingmode et pttrackingdans votre requête d’URL de Bootstrap.
seo-description: Vous pouvez activer le suivi des publicités côté client en ajoutant les paramètres de version pttrackingmode et pttrackingdans votre requête d’URL de Bootstrap.
seo-title: Activation du suivi des publicités côté client
title: Activation du suivi des publicités côté client
uuid: 0a825756-1d9a-43c5-bc22-9b366f39fdbb
translation-type: tm+mt
source-git-commit: e1e33d3ac0aad44859cd49566331524da72ac7e4
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 1%

---


# Activer le suivi des publicités côté client {#enable-client-side-ad-tracking}

Vous pouvez activer le suivi des publicités côté client en ajoutant les paramètres `pttrackingmode` et `pttrackingversion` à votre requête d’URL de Bootstrap.

Lorsque le suivi des publicités côté client est activé, vous pouvez également récupérer les métadonnées de suivi des publicités à l’aide de l’URL de l’API de suivi. Pour plus de détails, voir [Paramètres de Requête](/help/primetime-ad-insertion/~old-msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md).

Pour effectuer le suivi des publicités côté client, utilisez l’URL de l’API de suivi.

1. Ajoutez les paramètres de requête suivants à l’URL de demande du serveur de manifeste :

   * `pttrackingmode=simple`
   * `pttrackingversion={format version}`

Par exemple :

```URL
https://. . .?. . .&pttrackingmode=simple&pttrackingversion=v1
```
