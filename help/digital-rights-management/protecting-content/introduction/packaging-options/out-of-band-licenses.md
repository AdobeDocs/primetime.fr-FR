---
title: Licences hors bande
description: Licences hors bande
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# Licences hors bande {#out-of-band-licenses}

Grâce à Primetime DRM, vous pouvez mettre en oeuvre un processus dans lequel les clients obtiennent des licences prégénérées hors bande et éliminent ainsi la nécessité de déployer un serveur de licences. Pour prendre en charge ce flux de travaux, une option indiquant qu’aucun serveur de licences n’est disponible doit être spécifiée au moment de la création du pack. Cela empêche le client de tenter de demander une licence pour ce contenu à un serveur de licences.

Le contenu qui indique que le serveur de licences n’est pas disponible ne peut être lu que sur les clients DRM Primetime version 3.0 ou ultérieure. Les clients plus âgés doivent effectuer la mise à niveau pour lire ce contenu.
