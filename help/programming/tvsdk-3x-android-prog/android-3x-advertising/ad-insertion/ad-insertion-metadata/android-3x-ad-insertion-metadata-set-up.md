---
description: Utilisez la classe d’assistance AuditudeSettings, qui étend la classe MetadataNode, pour configurer les métadonnées Adobe Primetime et de prise de décision.
seo-description: Utilisez la classe d’assistance AuditudeSettings, qui étend la classe MetadataNode, pour configurer les métadonnées Adobe Primetime et de prise de décision.
seo-title: Configuration des métadonnées d’insertion de publicités
title: Configuration des métadonnées d’insertion de publicités
uuid: 7400813c-6af0-4c96-a6c7-d9ea1ba6a7b9
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# Configuration des métadonnées d’insertion de publicités {#set-up-ad-insertion-metadata}

Utilisez la classe d’assistance `AuditudeSettings`, qui étend la `MetadataNode` classe, pour configurer les métadonnées Adobe Primetime et de prise de décision.

>[!TIP]
>
>La prise de décision publicitaire Adobe Primetime était auparavant connue sous le nom d’Auditude.

Les métadonnées publicitaires se trouvent dans la `MediaResource.Metadata` propriété. Lors du démarrage de la lecture d’une nouvelle vidéo, votre application est chargée de définir les métadonnées publicitaires appropriées.

1. Créez l’ `AuditudeSettings` instance.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Définissez les paramètres de prise de décision publicitaire Adobe Primetime `mediaID`, `zoneID`, `<ph conkeyref="phrases/primetime-sdk-name"/>`et les paramètres de ciblage facultatifs.

   ```java
   auditudeSettings.setZoneId("yourZoneId"); 
   auditudeSettings.setMediaId("yourVideoId"); 
   auditudeSettings.setDefaultMediaId("defVideoId"); 
   auditudeSettings.setDomain("yourAuditudeDomain"); 
   
   // Optionally set user agent  
   auditudeSettings.setUserAgent("yourUserAgent"); 
   
   Metadata targetingParameters = new Metadata(); 
   targetingParameters.setValue("desired_param", "desired_value"); 
   auditudeSettings.setTargetingParameters(targetingParameters);
   ```

   >[!TIP]
   >
   >L’ID de média est utilisé par TVSDK sous la forme d’une chaîne, convertie en valeur md5, et utilisé pour la `u` valeur dans la demande d’URL de prise de décision et de Primetime. Par exemple :
   >
   >`https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Créez une `MediaResource` instance à l’aide de l’URL du flux média et des métadonnées publicitaires créées précédemment.

   ```java
   MediaResource mediaResource = new MediaResource( 
   "https://example.com/media/test_media.m3u8", MediaResource.Type.HLS, Metadata);
   ```

1. Chargez l’ `MediaResource` objet par le biais de la `MediaPlayer.replaceCurrentResource` méthode.

   Le `MediaPlayer` le chargement et le traitement du manifeste du flux média.

1. Lorsque le `MediaPlayer` à l’état INITIALIZED, obtenez les caractéristiques du flux média sous la forme d’une `MediaPlayerItem` instance par le biais de la `MediaPlayer.CurrentItem` méthode.
1. (Facultatif)  l’ `MediaPlayerItem` instance pour voir si le flux est en direct, qu’il comporte des pistes audio de remplacement ou qu’il soit protégé.

   Ces informations peuvent vous aider à préparer l’interface utilisateur pour la lecture. Par exemple, si vous savez qu’il existe deux pistes audio, vous pouvez inclure une commande d’interface utilisateur qui bascule entre ces pistes.

1. Appelez `MediaPlayer.prepareToPlay` pour le flux de travail publicitaire.

   Une fois les publicités résolues et placées sur la chronologie, le `MediaPlayer` à l’ `PREPARED` état.
1. Appelez `MediaPlayer.play` pour la lecture.
TVSDK comprend désormais des publicités lorsque votre média est lu.
