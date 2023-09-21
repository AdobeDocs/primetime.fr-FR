---
description: Utilisez la classe d’assistance AuditudeSettings, qui étend la classe MetadataNode, pour configurer les métadonnées de prise de décision publicitaire Adobe Primetime.
title: Configuration des métadonnées d’insertion de publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Configuration des métadonnées d’insertion de publicités {#set-up-ad-insertion-metadata}

Utilisation de la classe d’assistance `AuditudeSettings`, qui étend la variable `MetadataNode` pour configurer les métadonnées de prise de décision publicitaire Adobe Primetime.

>[!TIP]
>
>La prise de décision publicitaire Adobe Primetime était auparavant connue sous le nom d’Auditude.

Les métadonnées publicitaires se trouvent dans la variable `MediaResource.Metadata` . Lorsque vous démarrez la lecture d’une nouvelle vidéo, votre application est chargée de définir les métadonnées publicitaires correctes.

1. Créez la variable `AuditudeSettings` instance.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Définition de la prise de décision relative aux publicités Adobe Primetime `mediaID`, `zoneID`, `<ph conkeyref="phrases/primetime-sdk-name"/>`et les paramètres de ciblage facultatifs.

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
   >L’identifiant du média est utilisé par TVSDK sous forme de chaîne, converti en valeur md5 et utilisé pour la variable `u` dans la requête d’URL de prise de décision publicitaire Primetime. Par exemple :
   >
   >`https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Créez un `MediaResource` en utilisant l’URL du flux multimédia et les métadonnées publicitaires créées précédemment.

   ```java
   MediaResource mediaResource = new MediaResource( 
   "https://example.com/media/test_media.m3u8", MediaResource.Type.HLS, Metadata);
   ```

1. Chargez la variable `MediaResource` via l’objet `MediaPlayer.replaceCurrentResource` .

   La variable `MediaPlayer` démarre le chargement et le traitement du manifeste de flux multimédia.

1. Lorsque la variable `MediaPlayer` les transitions vers l’état INITIALIZED, obtenir les caractéristiques de diffusion multimédia sous la forme d’une `MediaPlayerItem` via l’instance `MediaPlayer.CurrentItem` .
1. (Facultatif) Interrogez le `MediaPlayerItem` pour voir si le flux est actif, qu’il possède des pistes audio alternatives ou qu’il soit protégé.

   Ces informations peuvent vous aider à préparer l’interface utilisateur pour la lecture. Par exemple, si vous savez qu’il existe deux pistes audio, vous pouvez inclure une commande de l’interface utilisateur qui bascule entre ces pistes.

1. Appeler `MediaPlayer.prepareToPlay` pour démarrer le workflow publicitaire.

   Une fois les publicités résolues et placées dans la chronologie, la variable `MediaPlayer` les transitions vers la `PREPARED` état.
1. Appeler `MediaPlayer.play` pour démarrer la lecture.
TVSDK comprend désormais des publicités lorsque votre média est lu.
