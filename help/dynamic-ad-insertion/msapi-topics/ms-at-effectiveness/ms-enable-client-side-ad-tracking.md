---
description: Vous pouvez activer le suivi des publicités côté client en ajoutant les paramètres de version pttrackingmode et pttrackingdans votre requête d'URL d'amorçage.
seo-description: Vous pouvez activer le suivi des publicités côté client en ajoutant les paramètres de version pttrackingmode et pttrackingdans votre requête d'URL d'amorçage.
seo-title: Activation du suivi des publicités côté client
title: Activation du suivi des publicités côté client
uuid: 0a825756-1d9a-43c5-bc22-9b366f39fdbb
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Activation du suivi des publicités côté client {#enable-client-side-ad-tracking}

Vous pouvez activer le suivi des publicités côté client en ajoutant les `pttrackingmode` paramètres et les `pttrackingversion` paramètres à votre requête d&#39;URL d&#39;amorçage.

Lorsque le suivi des publicités côté client est activé, vous pouvez également récupérer les métadonnées de suivi des publicités à l’aide de l’URL de l’API de suivi. Pour plus d’informations, voir Paramètres [de](../../msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md)Requête.

Pour effectuer le suivi des publicités côté client, utilisez l’URL de l’API de suivi.

1. Ajouter les paramètres de requête suivants à l’URL de demande de serveur de manifeste :

   * `pttrackingmode=simple`
   * `pttrackingversion={format version}`

Par exemple :

```
https://. . .?. . .&pttrackingmode=simple&pttrackingversion=v1
```
