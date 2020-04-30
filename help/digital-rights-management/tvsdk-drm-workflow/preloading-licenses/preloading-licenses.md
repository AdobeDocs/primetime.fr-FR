---
seo-title: Présentation des licences de Pré-chargement pour la lecture hors ligne
title: Présentation des licences de Pré-chargement pour la lecture hors ligne
uuid: 71e5169b-7f70-4723-9f9b-fdff822c5876
translation-type: tm+mt
source-git-commit: 9bbcb228d3367fbf53de811bf2941ca653ce3b0e

---


# Licences de Pré-chargement pour la lecture hors ligne {#pre-loading-licenses-for-offline-playback}

Vous pouvez précharger les licences requises pour lire le contenu protégé par Primetime DRM. Les licences préchargées permettent aux utilisateurs de vue le contenu, qu’ils disposent ou non d’une connexion Internet active.

Le processus de préchargement lui-même *nécessite* une connexion Internet. Vous pouvez précharger `DRMManager.loadVoucher()` les licences à l’avance. Par la suite, lorsque le client souhaite lire le contenu souhaité, le système DRM a été préamorcé et peut lire le contenu protégé immédiatement.
