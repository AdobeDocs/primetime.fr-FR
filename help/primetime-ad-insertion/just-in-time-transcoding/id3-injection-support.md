---
description: Le transcodage juste à temps peut injecter des métadonnées minutées ID3 dans les créations publicitaires afin de faciliter le suivi des publicités côté client.
title: Utilisation du transcodage juste à temps pour injecter des balises de métadonnées temporelles ID3
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Utilisation du transcodage juste à temps pour injecter des balises de métadonnées temporelles ID3 {#using-crs-to-inject-id-timed-metadata-tags}

CRS peut injecter des métadonnées minutées ID3 dans les créations publicitaires afin de faciliter le suivi des publicités côté client.

Le lecteur client lit les métadonnées ID3 pour activer le suivi des publicités avec précision d’image.

>[!NOTE]
>
>Fonctions d’injection de métadonnées minutées ID3 uniquement pour Safari/iOS.

## Processus pour CRS pour l’injection ID3 {#workflow-for-crs-for-id3-injection}

Si l’Ad Insertion Primetime reçoit la variable `ptplayer=ios-mobileweb` , il injectera des paquets ID3 dans la publicité transcodée avant de la transférer vers le réseau de diffusion de contenu de stockage de publicités approprié.
