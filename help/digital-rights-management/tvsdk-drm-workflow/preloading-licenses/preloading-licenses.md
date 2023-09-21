---
title: Présentation des licences de préchargement pour la lecture hors ligne
description: Présentation des licences de préchargement pour la lecture hors ligne
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---

# Licences de préchargement pour la lecture hors ligne {#pre-loading-licenses-for-offline-playback}

Vous pouvez précharger les licences requises pour lire le contenu protégé par Primetime DRM. Les licences préchargées permettent aux utilisateurs d’afficher le contenu s’ils disposent ou non d’une connexion Internet active.

Le processus de préchargement lui-même *does* nécessite une connexion Internet. Vous pouvez utiliser `DRMManager.loadVoucher()` avant le chargement des licences. Par la suite, lorsque le client souhaite lire le contenu souhaité, le système DRM a été préamorcé et peut lire le contenu protégé immédiatement.
