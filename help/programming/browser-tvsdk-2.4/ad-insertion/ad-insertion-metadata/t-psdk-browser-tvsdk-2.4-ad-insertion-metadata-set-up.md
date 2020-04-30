---
description: Utilisez la classe d’assistance AuditudeSettings pour configurer les métadonnées Adobe Primetime et de prise de décision.
seo-description: Utilisez la classe d’assistance AuditudeSettings pour configurer les métadonnées Adobe Primetime et de prise de décision.
seo-title: Configuration des métadonnées d’insertion de publicités
title: Configuration des métadonnées d’insertion de publicités
uuid: fc37e0ae-6acf-4a78-a468-f7b5b123b45e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Configuration des métadonnées d’insertion de publicités{#set-up-ad-insertion-metadata}

Utilisez la classe d’assistance AuditudeSettings pour configurer les métadonnées Adobe Primetime et de prise de décision.

>[!TIP]
>
>Auparavant, la prise de décision publicitaire d’Adobe Primetime était connue sous le nom d’Auditude.

1. Créez l’ `AuditudeSettings` instance.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Définissez les paramètres de ciblage facultatifs MediaID, zoneID, domain et Adobe Primetime pour la prise de décision publicitaire.

   ```js
   auditudeSettings.domain = "yourdomain"; 
   auditudeSettings.mediaId = "mediaid"; 
   auditudeSettings.zoneId = "zoneid";
   ```

1. Créez une `MediaResource` instance à l’aide de l’URL du flux média et des métadonnées publicitaires créées précédemment.

   ```js
   mediaResource = new AdobePSDK.MediaResource ( 
         resourceUrl, 
         resourceType,  
         auditudeSettings);
   ```

1. Chargez l’ `MediaResource` objet par le biais de la `MediaPlayer.replaceCurrentResource(resource)` méthode.

   Les `MediaPlayer` débuts de chargement et de traitement du manifeste de flux média.

1. Lorsque l’état INITIALISÉ est `MediaPlayer` transition, obtenez les caractéristiques du flux média sous la forme d’une `MediaPlayerItem` instance via l’ `MediaPlayer.CurrentItem` attribut.
1. (Facultatif) Requête l’ `MediaPlayerItem` instance pour déterminer si le flux est actif, qu’il comporte ou non des pistes audio de remplacement.

   Ces informations peuvent vous aider à préparer l’interface utilisateur à la lecture. Par exemple, si vous savez qu&#39;il y a deux pistes audio, vous pouvez inclure une commande d&#39;interface utilisateur qui bascule entre ces pistes.

1. Appelez `MediaPlayer.prepareToPlay` pour début le processus publicitaire.

   Une fois les publicités résolues et placées sur la chronologie, les `  MediaPlayer ` transitions sont à l’état PRÉPARÉ.
1. Appelez `MediaPlayer.play` pour début de la lecture.
Le kit TVSDK du navigateur comprend désormais des publicités lorsque votre média est lu.
