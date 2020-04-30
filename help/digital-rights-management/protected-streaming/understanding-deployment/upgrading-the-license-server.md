---
seo-title: Mise à niveau d’Adobe Primetime DRM Server for Protected Streaming
title: Mise à niveau d’Adobe Primetime DRM Server for Protected Streaming
uuid: 5c507ae3-d1d9-40ad-ba97-501ec92b45dc
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Mise à niveau d’Adobe Primetime DRM Server for Protected Streaming{#upgrading-the-adobe-primetime-drm-server-for-protected-streaming}

Si vous souhaitez mettre à niveau un serveur qui exécute le serveur DRM Primetime pour la diffusion en flux continu protégé, vous devez remplacer le `flashaccessserver.war` fichier qui a été déployé sur votre serveur d’applications par le fichier qui a été inclus avec le DRM Primetime le plus récent.

Si vous souhaitez utiliser les nouvelles options de configuration, vous devez mettre à jour celle de votre serveur `flashaccess-tenant.xml`. Vous devez également mettre à jour [!DNL jsafe.dll] ou [!DNL libjsafe.so] avec la version qui a été incluse avec la dernière version de DRM de Primetime.
