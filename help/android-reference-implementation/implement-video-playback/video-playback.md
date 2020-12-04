---
seo-title: Opérations essentielles de lecture vidéo
title: Opérations essentielles de lecture vidéo
description: PlaybackManager fournit des opérations essentielles de flux continu HLS
seo-description: PlaybackManager fournit des opérations essentielles de flux continu HLS
uuid: 7ac93f1f-9233-4462-a4be-528d1aa524a9
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# Opérations essentielles de lecture vidéo {#essential-operations-of-video-playback}

PlaybackManager fournit les opérations essentielles de flux continu HLS :

* Appelle le [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html), qui peut répondre de manière appropriée aux événements vidéo.
* Fournit des opérations de lecture telles que la lecture, la mise en pause et la recherche.
* Renvoie les informations relatives au lecteur, telles que l’état du lecteur, la plage de lecture et le flux vidéo en direct.
* Détermine si ABR est activé et définit les paramètres de contrôle ABR et buffer en fonction des données de configuration fournies.
* Détermine si le contrôle de la mémoire tampon est activé et définit les paramètres de contrôle de la mémoire tampon en fonction des données de configuration fournies.