---
title: Mise à niveau du serveur DRM Adobe Primetime pour la diffusion en continu protégée
description: Mise à niveau du serveur DRM Adobe Primetime pour la diffusion en continu protégée
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Mise à niveau du serveur DRM Adobe Primetime pour la diffusion en continu protégée{#upgrading-the-adobe-primetime-drm-server-for-protected-streaming}

Si vous souhaitez mettre à niveau un serveur qui exécute le serveur DRM Primetime pour la diffusion protégée, vous devez remplacer la variable `flashaccessserver.war` qui a été déployé sur votre serveur d’applications avec le fichier qui a été inclus avec le dernier DRM Primetime.

Si vous souhaitez utiliser les nouvelles options de configuration, vous devez mettre à jour le `flashaccess-tenant.xml`. Vous devez également mettre à jour [!DNL jsafe.dll] ou [!DNL libjsafe.so] avec la version qui a été incluse avec le dernier DRM Primetime.
