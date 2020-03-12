---
description: La relecture de  en mode plein (FER) est une ressource VOD qui agit comme une ressource en direct/DVR. Votre application doit donc prendre les mesures nécessaires pour s’assurer que les publicités sont correctement placées.
seo-description: La relecture de  en mode plein (FER) est une ressource VOD qui agit comme une ressource en direct/DVR. Votre application doit donc prendre les mesures nécessaires pour s’assurer que les publicités sont correctement placées.
seo-title: Activer les publicités en  de lecture en plein
title: Activer les publicités en  de lecture en plein
uuid: 70e463bd-332c-4f91-ac05-03e79c0939a4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Activer les publicités en  de lecture en plein{#enable-ads-in-full-event-replay}

La relecture de  en mode plein (FER) est une ressource VOD qui agit comme une ressource en direct/DVR. Votre application doit donc prendre les mesures nécessaires pour s’assurer que les publicités sont correctement placées.

Pour le contenu en direct, TVSDK utilise les métadonnées/indices du manifeste pour déterminer l’emplacement des publicités. Cependant, il arrive que le contenu dynamique/linéaire ressemble au contenu VOD. Par exemple, lorsque le contenu en direct se termine, une `EXT-X-ENDLIST` balise est ajoutée au manifeste en direct. Pour HLS, la `EXT-X-ENDLIST` balise signifie que le flux est un flux VOD. TVSDK ne peut pas automatiquement différencier ce flux d’un flux VOD normal pour insérer correctement des publicités.

Votre application doit indiquer à TVSDK si le contenu est en direct ou VOD en spécifiant le `AdSignalingMode`.

Dans le cas d’un flux FER, le serveur Adobe Primetime de prise de décision publicitaire ne doit pas fournir le de coupures publicitaires à insérer dans la chronologie avant de commencer la lecture. Il s’agit du processus typique pour le contenu VOD. Au lieu de cela, en spécifiant un mode de signalisation différent, TVSDK lit tous les points de repère du manifeste FER et va au serveur d’annonces pour chaque point de repère pour demander une coupure publicitaire. Ce processus est similaire au contenu en direct/DVR.

Outre chaque requête associée à un point de repère, TVSDK effectue une demande de publicité supplémentaire pour les publicités preroll.

1. A partir d’une source externe, telle que vCMS, obtenez le mode de signalisation à utiliser.
1. Créez les métadonnées liées à la publicité.
1. Si le comportement par défaut doit être remplacé, spécifiez le comportement `AdSignalingMode` en utilisant `AdvertisingMetadata.setSignalingMode`.

   Les valeurs valides sont `DEFAULT, SERVER_MAP`, et `MANIFEST_CUES`.

   Vous devez définir le mode de signalisation de la publicité avant d’appeler `prepareToPlay`. Une fois que le TVSDK a résolu et placé les publicités dans le plan de montage chronologique, les modifications apportées au mode de signalisation publicitaire sont ignorées. Définissez le mode lorsque vous créez l’ `AuditudeSettings` objet.

1. Poursuivez la lecture.

<!--<a id="example_3567B4A0D53E4DA99C10C13244454026"></a>-->

