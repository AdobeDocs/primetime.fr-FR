---
title: DRM Primetime sur le client
description: DRM Primetime sur le client
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---


# DRM Primetime sur le client{#primetime-drm-on-the-client}

Une application TVSDK Primetime qui lit du contenu protégé doit d’abord appeler les API DRM de Primetime pour lancer le flux de travail en vue de la consommation de licences et de la lecture de contenu protégé. Dans ce flux de travaux, Primetime DRM sur le client construit une demande de licence à partir des métadonnées du contenu protégé, puis l’envoie au serveur de licences DRM Primetime.

Avant d’émettre la demande de licence, le client peut éventuellement effectuer l’authentification/l’autorisation nécessaires (selon les règles de votre entreprise).
