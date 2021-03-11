---
title: Mise à niveau du serveur DRM Adobe Primetime pour la diffusion en flux continu protégée
description: Mise à niveau du serveur DRM Adobe Primetime pour la diffusion en flux continu protégée
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Mise à niveau du serveur DRM Adobe Primetime pour la diffusion en flux continu protégée{#upgrading-the-adobe-primetime-drm-server-for-protected-streaming}

Si vous souhaitez mettre à niveau un serveur qui exécute le serveur DRM Primetime pour la diffusion en flux continu protégé, vous devez remplacer le fichier `flashaccessserver.war` déployé sur votre serveur d’applications par le fichier qui a été inclus avec le dernier DRM Primetime.

Si vous souhaitez utiliser les nouvelles options de configuration, vous devez mettre à jour `flashaccess-tenant.xml` de votre serveur. Vous devez également mettre à jour [!DNL jsafe.dll] ou [!DNL libjsafe.so] avec la version qui a été incluse avec la dernière DRM de Primetime.
