---
seo-title: DRM Primetime sur le client
title: DRM Primetime sur le client
uuid: 472180ad-6596-4a24-aa51-7909a75a5e10
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# DRM Primetime sur le client{#primetime-drm-on-the-client}

Une application TVSDK Primetime qui lit du contenu protégé doit d’abord appeler les API DRM Primetime pour lancer le flux de travaux en vue de la consommation de licence et de la lecture de contenu protégé. Dans ce flux de travaux, le DRM Primetime sur le client construit une demande de licence à partir des métadonnées du contenu protégé, puis l’envoie au serveur de licences DRM Primetime.

Avant d’émettre la demande de licence, le client peut éventuellement effectuer l’authentification ou l’autorisation nécessaires (selon vos règles de fonctionnement).
