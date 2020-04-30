---
description: CRS peut injecter des métadonnées minutées ID3 au format HLS dans les éléments créatifs des publicités afin de faciliter le suivi des publicités côté client.
seo-description: CRS peut injecter des métadonnées minutées ID3 au format HLS dans les éléments créatifs des publicités afin de faciliter le suivi des publicités côté client.
seo-title: Utilisation de CRS pour injecter des balises de métadonnées minutées ID3
title: Utilisation de CRS pour injecter des balises de métadonnées minutées ID3
uuid: 491bbb9e-15de-4871-baa1-f7bb0ea0dde2
translation-type: tm+mt
source-git-commit: c2216a5089d23ca1fcbb77c87b4a01a6fa1807ff

---


# Utilisation de CRS pour injecter des balises de métadonnées minutées ID3 {#using-crs-to-inject-id-timed-metadata-tags}

CRS peut injecter des métadonnées minutées ID3 au format HLS dans les éléments créatifs des publicités afin de faciliter le suivi des publicités côté client.

Le lecteur client lit les métadonnées ID3 pour activer le suivi des publicités avec précision d’image.

>[!NOTE]
>
>L’injection de métadonnées minutées ID3 fonctionne uniquement sur Safari sur iOS.

## Workflow pour CRS pour l&#39;injection ID3 {#workflow-for-crs-for-id3-injection}

Le flux de travaux pour l’injection ID3 est identique à celui des Workflows [détaillés pour la restauration JIT.](../creative-repackaging-service/jit-repackage.md) Si le serveur de manifeste reçoit le `ptplayer=ios-mobileweb` paramètre, il indique à CRS d’injecter des paquets ID3 dans la publicité transcodée et créative avant de la télécharger sur le serveur CDN.

>[!NOTE]
>
>Dans une configuration multiCDN, le serveur de manifeste utilise le `ptcdn` paramètre de l’URL d’amorçage pour identifier le serveur CDN à utiliser pour télécharger la création publicitaire.