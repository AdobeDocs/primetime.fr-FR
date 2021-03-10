---
description: Utilisez la classe d’assistance AuditudeSettings pour configurer les métadonnées de prise de décision des publicités Adobe Primetime.
title: Configuration des métadonnées d’insertion de publicités
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Configurer les métadonnées d’insertion de publicité{#set-up-ad-insertion-metadata}

Utilisez la classe d’assistance AuditudeSettings pour configurer les métadonnées de prise de décision des publicités Adobe Primetime.

>[!TIP]
>
>La prise de décision publicitaire Adobe Primetime était auparavant connue sous le nom d’Auditude.

1. Créez l&#39;instance `AuditudeSettings`.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Définissez les paramètres de ciblage facultatifs MediaID, zoneID, domain et Adobe Primetime pour la prise de décision publicitaire.

   ```js
   auditudeSettings.domain = "yourdomain"; 
   auditudeSettings.mediaId = "mediaid"; 
   auditudeSettings.zoneId = "zoneid";
   ```

1. Créez une instance `MediaResource` en utilisant l’URL du flux média et les métadonnées publicitaires créées précédemment.

   ```js
   mediaResource = new AdobePSDK.MediaResource ( 
         resourceUrl, 
         resourceType,  
         auditudeSettings);
   ```

1. Chargez l&#39;objet `MediaResource` par l&#39;intermédiaire de la méthode `MediaPlayer.replaceCurrentResource(resource)`.

   Le `MediaPlayer` début le chargement et le traitement du manifeste de flux média.

1. Lorsque `MediaPlayer` transition à l&#39;état INITIALISÉ, obtenez les caractéristiques du flux média sous la forme d&#39;une instance `MediaPlayerItem` par le biais de l&#39;attribut `MediaPlayer.CurrentItem`.
1. (Facultatif) Requête l’instance `MediaPlayerItem` pour déterminer si le flux est actif, qu’il possède ou non d’autres pistes audio.

   Ces informations peuvent vous aider à préparer l’interface utilisateur à la lecture. Par exemple, si vous savez qu&#39;il y a deux pistes audio, vous pouvez inclure une commande d&#39;interface utilisateur qui bascule entre ces pistes.

1. Appelez `MediaPlayer.prepareToPlay` pour début du processus publicitaire.

   Une fois les publicités résolues et placées dans la chronologie, `  MediaPlayer ` transition à l’état PRÉPARÉ.
1. Appelez `MediaPlayer.play` pour début de la lecture.
Le kit TVSDK du navigateur comprend désormais des publicités lorsque votre média est lu.
