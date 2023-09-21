---
description: Adobe Primetime DRM Server for Protected Streaming est une mise en oeuvre de serveur de licences basée sur le SDK DRM Primetime. Ce serveur émet des licences pour le contenu protégé aux clients Primetime DRM.
title: À propos du serveur DRM Adobe Primetime pour la diffusion en continu protégée
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# À propos du serveur DRM Adobe Primetime pour la diffusion en continu protégée{#about-adobe-primetime-drm-server-for-protected-streaming}

Adobe Primetime DRM Server for Protected Streaming est une mise en oeuvre de serveur de licences basée sur le SDK DRM Primetime. Ce serveur émet des licences pour le contenu protégé aux clients Primetime DRM.

Le serveur DRM Primetime pour la diffusion protégée prend en charge plusieurs clients. Vous pouvez héberger un seul serveur pour le compte de plusieurs éditeurs de contenu, chacun disposant de ses propres paramètres de configuration. En outre, le serveur prend en charge les composants d’autorisation personnalisés afin que vous puissiez exécuter une logique personnalisée avant l’émission d’une licence.

Ce serveur est destiné à être utilisé avec la diffusion en continu HTTP. Par conséquent, cette mise en oeuvre de serveur ne prend pas en charge toutes les fonctionnalités disponibles dans Primetime DRM. Par exemple, il ne prend pas en charge les demandes d’authentification des utilisateurs, les stratégies multiples, les licences liées au domaine, le chaînage de licences ou les messages de synchronisation.

>[!NOTE]
>
>Adobe Primetime DRM s’appelait auparavant Accès aux Adobes, et avant cela, Flash Access.
