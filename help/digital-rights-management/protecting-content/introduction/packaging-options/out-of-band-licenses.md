---
title: Licences hors bande
description: Licences hors bande
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Licences hors bande {#out-of-band-licenses}

Grâce à Primetime DRM, vous pouvez mettre en oeuvre un processus dans lequel les clients obtiennent des licences prégénérées hors bande et éliminent ainsi la nécessité de déployer un serveur de licences. Pour prendre en charge ce workflow, une option indiquant qu’aucun serveur de licences n’est disponible doit être spécifiée au moment du conditionnement. Cela empêche le client de tenter de demander une licence pour ce contenu à un serveur de licences.

Le contenu qui indique la non-disponibilité d’un serveur de licences ne peut être lu que sur les clients Primetime DRM version 3.0 ou ultérieure. Les clients plus anciens doivent effectuer une mise à niveau pour lire ce contenu.
