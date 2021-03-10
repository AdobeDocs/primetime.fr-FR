---
description: Le transcodage juste à temps peut injecter des métadonnées minutées ID3 dans les créations publicitaires afin de faciliter le suivi des publicités côté client.
title: Utilisation du transcodage juste à temps pour insérer des balises de métadonnées temporelles ID3
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Utilisation du transcodage juste à temps pour injecter des balises de métadonnées minutées ID3 {#using-crs-to-inject-id-timed-metadata-tags}

CRS peut injecter des métadonnées minutées ID3 dans les créatifs publicitaires afin de faciliter le suivi des publicités côté client.

Le lecteur client lit les métadonnées ID3 pour activer le suivi des publicités avec précision d’image.

>[!NOTE]
>
>Les fonctions d’injection de métadonnées minutées ID3 ne sont disponibles que pour Safari/iOS.

## Processus de CRS pour l&#39;injection ID3 {#workflow-for-crs-for-id3-injection}

Si l’Ad Insertion Primetime reçoit le paramètre `ptplayer=ios-mobileweb`, il injectera des paquets ID3 dans le fichier publicitaire transcodé et créatif avant de le télécharger sur le réseau de diffusion de contenu de l’enregistrement publicitaire approprié.
