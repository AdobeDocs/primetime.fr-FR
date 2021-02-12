---
description: Le transcodage juste à temps peut injecter des métadonnées minutées ID3 dans les créations publicitaires afin de faciliter le suivi des publicités côté client.
seo-description: Le transcodage juste à temps peut injecter des métadonnées minutées ID3 au format HLS dans des éléments créatifs pour faciliter le suivi des annonces côté client.
seo-title: Utilisation du transcodage juste à temps pour insérer des balises de métadonnées temporelles ID3
title: Utilisation du transcodage juste à temps pour insérer des balises de métadonnées temporelles ID3
uuid: 491bbb9e-15de-4871-baa1-f7bb0ea0dde2
translation-type: tm+mt
source-git-commit: 0f98b9848f1764e7c66e3692d8a845513493597f
workflow-type: tm+mt
source-wordcount: '121'
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
