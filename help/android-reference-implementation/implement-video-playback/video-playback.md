---
title: Opérations essentielles de lecture vidéo
description: PlaybackManager fournit des opérations essentielles de diffusion HLS en continu
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Opérations essentielles de lecture vidéo {#essential-operations-of-video-playback}

PlaybackManager fournit les opérations essentielles de diffusion HLS en continu :

* Appelle le [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html), qui peut répondre de manière appropriée aux événements vidéo.
* Permet d’effectuer des opérations de lecture telles que la lecture, la mise en pause et la recherche.
* Renvoie les informations relatives au lecteur, telles que l’état du lecteur, la plage de lecture et la diffusion vidéo en direct.
* Détermine si ABR est activé et définit les paramètres de contrôle ABR et de mémoire tampon en fonction des données de configuration fournies.
* Détermine si le contrôle de la mémoire tampon est activé et définit les paramètres du contrôle de la mémoire tampon en fonction des données de configuration fournies.
