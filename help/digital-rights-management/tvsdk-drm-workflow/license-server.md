---
title: Serveur de licences DRM Primetime
description: Serveur de licences DRM Primetime
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---

# Serveur de licences DRM Primetime {#primetime-drm-license-server}

Le serveur de licences DRM Primetime est créé à partir du SDK Java DRM Primetime. Ce serveur consomme les demandes de licence des clients demandant l’accès au contenu protégé. Le serveur peut analyser et manipuler la stratégie DRM depuis la demande de licence, afin de modifier ou de remplacer la stratégie avant d’utiliser la stratégie pour générer une licence pour le client qui la demande.

Pour déployer un serveur de licences DRM Primetime, il doit d’abord répondre aux exigences suivantes : **Règles de conformité et de robustesse des Adobes** pour Primetime DRM. Adobe propose également un service de licence Primetime DRM hébergé appelé [Primetime Cloud DRM](../cloud-quick-start/whats-included.md), que vous pouvez utiliser comme alternative à l’hébergement de votre propre serveur de licences.
