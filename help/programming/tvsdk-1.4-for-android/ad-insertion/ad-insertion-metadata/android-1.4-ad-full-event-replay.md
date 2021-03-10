---
description: La relecture en événement complet (FER) est une ressource VOD qui agit comme une ressource en direct/DVR. Votre application doit donc prendre des mesures pour s’assurer que les publicités sont placées correctement.
title: Activer les publicités en lecture événement complet
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# Activer les publicités en lecture à événement complet{#enable-ads-in-full-event-replay}

La relecture en événement complet (FER) est une ressource VOD qui agit comme une ressource en direct/DVR. Votre application doit donc prendre des mesures pour s’assurer que les publicités sont placées correctement.

Pour le contenu en direct, TVSDK utilise les métadonnées/indices du manifeste pour déterminer l’emplacement des publicités. Cependant, il arrive que le contenu en direct/linéaire ressemble au contenu VOD. Par exemple, lorsque le contenu en direct se termine, une balise `EXT-X-ENDLIST` est ajoutée au manifeste en direct. Pour HLS, la balise `EXT-X-ENDLIST` signifie que le flux est un flux VOD. TVSDK ne peut pas automatiquement différencier ce flux d’un flux VOD normal pour insérer correctement des publicités.

Votre application doit indiquer à TVSDK si le contenu est actif ou VOD en spécifiant `AdSignalingMode`.

Dans le cas d’un flux FER, le serveur de prise de décision publicitaire Adobe Primetime ne doit pas fournir la liste des coupures publicitaires qui doivent être insérées dans la chronologie avant de commencer la lecture. Il s’agit du processus typique pour le contenu VOD. Au lieu de cela, en spécifiant un mode de signalisation différent, TVSDK lit tous les indices du manifeste FER et va au serveur d’annonces pour chaque indice pour demander une coupure publicitaire. Ce processus est similaire au contenu en direct/DVR.

Outre chaque demande associée à un point de repère, TVSDK effectue une demande de publicité supplémentaire pour les publicités preroll.

1. A partir d’une source externe, telle que vCMS, obtenez le mode de signalisation à utiliser.
1. Créez les métadonnées liées à la publicité.
1. Si le comportement par défaut doit être remplacé, spécifiez `AdSignalingMode` en utilisant `AdvertisingMetadata.setSignalingMode`.

   Les valeurs valides sont `DEFAULT, SERVER_MAP` et `MANIFEST_CUES`.

   Vous devez définir le mode de signalisation de la publicité avant d&#39;appeler `prepareToPlay`. Après les débuts TVSDK de résolution et de placement des publicités dans la chronologie, les modifications apportées au mode de signalisation publicitaire sont ignorées. Définissez le mode lorsque vous créez l&#39;objet `AuditudeSettings`.

1. Poursuivez la lecture.

<!--<a id="example_3567B4A0D53E4DA99C10C13244454026"></a>-->

