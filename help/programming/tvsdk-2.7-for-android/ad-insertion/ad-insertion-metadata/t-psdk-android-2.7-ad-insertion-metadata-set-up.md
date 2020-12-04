---
description: Utilisez la classe d’assistance AuditudeSettings, qui étend la classe MetadataNode, pour configurer les métadonnées de prise de décision des publicités Adobe Primetime.
seo-description: Utilisez la classe d’assistance AuditudeSettings, qui étend la classe MetadataNode, pour configurer les métadonnées de prise de décision des publicités Adobe Primetime.
seo-title: Configuration des métadonnées d’insertion de publicités
title: Configuration des métadonnées d’insertion de publicités
uuid: 5c807fad-4927-4547-b58c-f37e505e651c
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---


# Configurer les métadonnées d&#39;insertion de publicité {#set-up-ad-insertion-metadata}

Utilisez la classe d’assistance AuditudeSettings, qui étend la classe MetadataNode, pour configurer les métadonnées de prise de décision des publicités Adobe Primetime.

>[!TIP]
>
>La prise de décision publicitaire Adobe Primetime était auparavant connue sous le nom d’Auditude.

Les métadonnées publicitaires se trouvent dans la propriété `MediaResource.Metadata`. Lors du démarrage de la lecture d’une nouvelle vidéo, votre application est chargée de définir les métadonnées publicitaires appropriées.

1. Créez l&#39;instance `AuditudeSettings`.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Définissez les paramètres de ciblage facultatifs pour la prise de décision de publicité Adobe Primetime `mediaID`, `zoneID`, `<ph conkeyref="phrases/primetime-sdk-name"/>`.

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
   >L’ID de média est utilisé par TVSDK sous la forme d’une chaîne, convertie en valeur md5, et est utilisé pour la valeur `u` dans la demande d’URL de prise de décision et de Primetime. Par exemple :
   >
   >
   >` https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Créez une instance `MediaResource` en utilisant l’URL du flux média et les métadonnées publicitaires créées précédemment.

   ```java
   MediaResource mediaResource = new MediaResource( 
   "https://example.com/media/test_media.m3u8", MediaResource.Type.HLS, Metadata);
   ```

1. Chargez l&#39;objet `MediaResource` par l&#39;intermédiaire de la méthode `MediaPlayer.replaceCurrentResource`.

   Le `MediaPlayer` début le chargement et le traitement du manifeste de flux média.

1. Lorsque `MediaPlayer` transition à l&#39;état INITIALISÉ, obtenez les caractéristiques du flux média sous la forme d&#39;une instance `MediaPlayerItem` par le biais de la méthode `MediaPlayer.CurrentItem`.
1. (Facultatif) Requête l’instance `MediaPlayerItem` pour déterminer si le flux est actif, qu’il comporte des pistes audio de remplacement ou si le flux est protégé.

   Ces informations peuvent vous aider à préparer l’interface utilisateur à la lecture. Par exemple, si vous savez qu&#39;il y a deux pistes audio, vous pouvez inclure une commande d&#39;interface utilisateur qui bascule entre ces pistes.

1. Appelez `MediaPlayer.prepareToPlay` pour début du processus publicitaire.

   Une fois les publicités résolues et placées dans la chronologie, l&#39;`MediaPlayer` transition à l&#39;état `PREPARED`.
1. Appelez `MediaPlayer.play` pour début de la lecture.

TVSDK comprend désormais des publicités lorsque votre média est lu.