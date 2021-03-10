---
description: Le serveur Adobe Primetime DRM Server pour la diffusion en flux continu protégée est une mise en oeuvre du serveur de licences basée sur le SDK DRM de Primetime. Ce serveur délivre des licences pour le contenu protégé aux clients DRM Primetime.
title: A propos du serveur DRM Adobe Primetime pour la diffusion en continu protégée
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---


# À propos du serveur DRM Adobe Primetime pour la diffusion en continu protégée{#about-adobe-primetime-drm-server-for-protected-streaming}

Le serveur Adobe Primetime DRM Server pour la diffusion en flux continu protégée est une mise en oeuvre du serveur de licences basée sur le SDK DRM de Primetime. Ce serveur délivre des licences pour le contenu protégé aux clients DRM Primetime.

Primetime DRM Server for Protected Streaming prend en charge plusieurs locataires. Vous pouvez héberger un serveur unique au nom de plusieurs éditeurs de contenu, chacun avec ses propres paramètres de configuration. En outre, le serveur prend en charge les composants d’autorisation personnalisés, de sorte que vous pouvez exécuter une logique personnalisée avant la délivrance d’une licence.

Ce serveur est destiné à être utilisé avec la diffusion en flux continu HTTP. Par conséquent, cette implémentation de serveur ne prend pas en charge toutes les fonctionnalités disponibles dans Primetime DRM. Par exemple, il ne prend pas en charge les demandes d’authentification des utilisateurs, les stratégies multiples, les licences liées aux domaines, le chaînage de licences ou les messages de synchronisation.

>[!NOTE]
>
>Adobe Primetime DRM s&#39;appelait auparavant Adobe Access, et avant cela, Flash Access.

