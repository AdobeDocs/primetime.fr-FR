---
seo-title: Présentation des licences de pré-chargement pour la lecture hors ligne
title: Présentation des licences de pré-chargement pour la lecture hors ligne
uuid: 71e5169b-7f70-4723-9f9b-fdff822c5876
translation-type: tm+mt
source-git-commit: 9bbcb228d3367fbf53de811bf2941ca653ce3b0e
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---


# Licences de pré-chargement pour la lecture hors ligne {#pre-loading-licenses-for-offline-playback}

Vous pouvez précharger les licences requises pour lire le contenu protégé par Primetime DRM. Les licences préchargées permettent aux utilisateurs de vue le contenu, qu’ils disposent ou non d’une principale connexion Internet.

Le processus de préchargement lui-même *nécessite* une connexion Internet. Vous pouvez utiliser `DRMManager.loadVoucher()` à l’avance pour précharger des licences. Par la suite, lorsque le client souhaite lire le contenu souhaité, le système DRM a été préamorcé et peut lire le contenu protégé immédiatement.
