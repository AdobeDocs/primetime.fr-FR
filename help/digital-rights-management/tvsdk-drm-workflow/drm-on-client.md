---
title: Primetime DRM sur le client
description: Primetime DRM sur le client
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# Primetime DRM sur le client{#primetime-drm-on-the-client}

Une application Primetime TVSDK qui lit du contenu protégé doit d’abord appeler les API Primetime DRM pour lancer le processus de consommation de licence et de lecture de contenu protégé. Dans ce processus, Primetime DRM sur le client construit une demande de licence à partir des métadonnées du contenu protégé, puis l’envoie au serveur de licences Primetime DRM.

Avant d’émettre la demande de licence, le client peut éventuellement effectuer l’authentification/autorisation nécessaire (en fonction de vos règles métier).
