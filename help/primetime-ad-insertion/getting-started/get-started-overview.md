---
title: Prise en main d’Adobe Primetime Ad Insertion
description: Prise en main d’Adobe Primetime Ad Insertion
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Prise en main d’Adobe Primetime Ad Insertion {#ptai-get-started}

Primetime Ad Insertion coordonne les systèmes qui fournissent du contenu et des publicités pour créer des expériences publicitaires en continu personnalisées, puis effectuer le suivi de la lecture des publicités pour vos annonceurs.

Primetime Ad Insertion interagit avec les applications clientes de diffusion vidéo en réécrivant des manifestes vidéo afin de fournir des publicités ciblées et des expériences personnalisées pour chaque visionneuse. Ces manifestes combinent du contenu et des publicités diffusés à partir d’un serveur de publicités et peuvent éventuellement inclure des métadonnées contenant des instructions détaillées de suivi des publicités. Primetime Ad Insertion prend en charge le suivi des publicités côté client et côté serveur.

Une fois le système correctement configuré, un workflow type peut se présenter comme suit :

1. L’application cliente génère une [URL du Bootstrap](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) avec des informations sur le flux vidéo et envoie une demande de GET à l’Ad Insertion Primetime.  L’Ad Insertion Primetime prend en charge HLS et DASH avec divers formats de signalisation publicitaire.

1. L’Ad Insertion Primetime répond en renvoyant le manifeste de contenu du CDN de l’éditeur à l’application cliente.

1. L’application cliente choisit les flux appropriés dans le manifeste généré à lire et envoie des requêtes à l’Ad Insertion Primetime.

1. Primetime Ad Insertion récupère le(s) flux(s) demandé(s) à partir du CDN de contenu, analyse/lit les informations de repère, effectue des appels au serveur de publicités et remplace les coupures publicitaires si nécessaire.

1. Primetime Ad Insertion normalise le manifeste en réécrivant les URL des ressources et en détectant si les créations publicitaires requièrent un transcodage, voir [Transcodage de publicité juste à temps](/help/primetime-ad-insertion/just-in-time-transcoding/jit-transcoding-overview.md).

1. Primetime Ad Insertion récupère les éléments créatifs publicitaires requis et insère les fragments appropriés dans les manifestes.

1. Primetime Ad Insertion envoie les manifestes assemblés finaux, y compris les publicités, à l’application cliente pour lecture.

1. La diffusion et la visibilité des publicités peuvent être mesurées via le suivi des publicités côté client ou côté serveur, voir [Configuration du suivi des publicités](/help/primetime-ad-insertion/getting-started/set-up-ad-tracking.md).

L’Ad Insertion Primetime prend en charge la plupart des configurations de client et de lecteur HLS/DASH. Pour plus d’informations sur les formats de signalisation de publicités spécifiques pris en charge, voir [Formats de repère pris en charge](/help/primetime-ad-insertion/getting-started/ad-insertion-live-linear-stream.md).
