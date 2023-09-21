---
description: Utilisez la classe d’assistance AuditudeSettings pour configurer les métadonnées de prise de décision publicitaire d’Adobe Primetime.
title: Configuration des métadonnées d’insertion de publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Configuration des métadonnées d’insertion de publicités{#set-up-ad-insertion-metadata}

Utilisez la classe d’assistance AuditudeSettings pour configurer les métadonnées de prise de décision publicitaire d’Adobe Primetime.

>[!TIP]
>
>La prise de décision publicitaire Adobe Primetime était auparavant connue sous le nom d’ Auditude .

1. Créez la variable `AuditudeSettings` instance.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Définissez les paramètres de ciblage facultatifs MediaID, zoneID, domaine et Adobe Primetime Ad Decisioning.

   ```js
   auditudeSettings.domain = "yourdomain"; 
   auditudeSettings.mediaId = "mediaid"; 
   auditudeSettings.zoneId = "zoneid";
   ```

1. Créez un `MediaResource` en utilisant l’URL du flux multimédia et les métadonnées publicitaires créées précédemment.

   ```js
   mediaResource = new AdobePSDK.MediaResource ( 
         resourceUrl, 
         resourceType,  
         auditudeSettings);
   ```

1. Chargez la variable `MediaResource` via l’objet `MediaPlayer.replaceCurrentResource(resource)` .

   La variable `MediaPlayer` démarre le chargement et le traitement du manifeste de flux multimédia.

1. Lorsque la variable `MediaPlayer` les transitions vers l’état INITIALIZED, obtenir les caractéristiques de diffusion multimédia sous la forme d’une `MediaPlayerItem` via l’instance `MediaPlayer.CurrentItem` attribut.
1. (Facultatif) Interrogez le `MediaPlayerItem` pour voir si le flux est actif, qu’il possède des pistes audio alternatives ou non.

   Ces informations peuvent vous aider à préparer l’interface utilisateur pour la lecture. Par exemple, si vous savez qu’il existe deux pistes audio, vous pouvez inclure une commande de l’interface utilisateur qui bascule entre ces pistes.

1. Appeler `MediaPlayer.prepareToPlay` pour démarrer le workflow publicitaire.

   Une fois les publicités résolues et placées dans la chronologie, la variable `  MediaPlayer ` passe à l’état PRÉPARÉ .
1. Appeler `MediaPlayer.play` pour démarrer la lecture.
Le TVSDK du navigateur inclut désormais des publicités lorsque votre média est lu.
