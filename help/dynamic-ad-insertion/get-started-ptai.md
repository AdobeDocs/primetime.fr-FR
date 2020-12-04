---
title: Commencer avec l’Ad Insertion Adobe Primetime
description: Prise en main de l’Ad Insertion Adobe Primetime
translation-type: tm+mt
source-git-commit: 2a9bb089cda2b315f91b30d5cab0db9b3e372799
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---


# Commencer avec l’Ad Insertion Adobe Primetime {#ptai-get-started}

L’Ad Insertion Primetime coordonne les systèmes qui fournissent du contenu et des publicités afin de créer des expériences publicitaires personnalisées en flux continu, puis de suivre la lecture des publicités pour vos annonceurs.

L’Ad Insertion Primetime interagit avec les applications clientes de diffusion vidéo en réécrivant des manifestes vidéo afin de fournir des publicités ciblées et des expériences personnalisées pour chaque visionneuse. Ces manifestes combinent le contenu et les publicités diffusés à partir d’un serveur d’annonces et peuvent éventuellement inclure des métadonnées contenant des instructions détaillées sur le suivi des publicités. L’Ad Insertion Primetime prend en charge le suivi des publicités côté client et côté serveur.

Une fois le système correctement configuré, un processus type peut se présenter comme suit :

1. L’application cliente génère une [URL du Bootstrap](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md) contenant des informations sur le flux vidéo et envoie une demande de GET à l’Ad Insertion Primetime.

1. L’Ad Insertion Primetime répond en renvoyant le manifeste de contenu du CDN de l’éditeur à l’application cliente.

1. L’application cliente choisit les flux appropriés dans le manifeste généré à lire et envoie des requêtes à l’Ad Insertion Primetime.

1. L’Ad Insertion Primetime récupère le(s) flux(s) demandé(s) à partir du CDN de contenu, analyse/lit les informations de repère, effectue des appels au serveur d’annonces et remplace les coupures publicitaires si nécessaire.

1. L’Ad Insertion Primetime normalise le manifeste en réécrivant les URL de ressources et en détectant si les créatifs publicitaires doivent être transcodés. <!-- see [Just-in-time ad transcoding](just-in-time-transcoding.md) and [packaging](just-in-time-repackaging.md).-->

1. L’Ad Insertion Primetime récupère les éléments créatifs publicitaires requis et insère les fragments appropriés dans les manifestes.

1. L’Ad Insertion Primetime diffuse les manifestes assemblés finaux, y compris les publicités, à l’application cliente pour lecture.

1. La diffusion et la capacité d&#39;affichage des publicités peuvent être mesurées via le suivi des publicités côté client ou côté serveur, voir [Configuration du suivi des publicités](set-up-ad-tracking.md).

L’Ad Insertion Primetime prend en charge la plupart des configurations client pour HLS/DASH.
