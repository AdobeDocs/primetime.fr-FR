---
description: CRS peut injecter des métadonnées minutées ID3 dans des annonces au format HLS afin de faciliter le suivi des publicités côté client.
title: Utilisation de CRS pour injecter des balises de métadonnées temporelles ID3
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Utilisation de CRS pour injecter des balises de métadonnées temporelles ID3 {#using-crs-to-inject-id-timed-metadata-tags}

CRS peut injecter des métadonnées minutées ID3 dans des annonces au format HLS afin de faciliter le suivi des publicités côté client.

Le lecteur client lit les métadonnées ID3 pour activer le suivi des publicités avec précision d’image.

>[!NOTE]
>
>L’injection de métadonnées minutées ID3 fonctionne uniquement sur Safari sur iOS.

## Processus pour CRS pour l’injection ID3 {#workflow-for-crs-for-id3-injection}

Le workflow d’injection ID3 est le même que dans [Workflows détaillés pour la correction JIT.](../~old-creative-repackaging-service/jit-repackage.md) Si le serveur de manifeste reçoit la variable `ptplayer=ios-mobileweb` , il indique à CRS d’injecter des paquets ID3 dans la publicité transcodée créative avant de la télécharger sur le serveur CDN.

>[!NOTE]
>
>Dans une configuration multi-CDN, le serveur manifeste utilise la variable `ptcdn` dans l’URL de bootstrap afin d’identifier le serveur CDN pour télécharger l’élément créatif publicitaire.