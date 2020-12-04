---
description: Pour que le résolveur d’annonces puisse fonctionner, les fournisseurs d’annonces, tels que la prise de décision d’annonces Adobe Primetime, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
seo-description: Pour que le résolveur d’annonces puisse fonctionner, les fournisseurs d’annonces, tels que la prise de décision d’annonces Adobe Primetime, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
seo-title: Métadonnées d’insertion publicitaire
title: Métadonnées d’insertion publicitaire
uuid: 3eb024c3-4bb5-4bee-943e-fe0c60379e60
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# Métadonnées d’insertion d’annonce {#ad-insertion-metadata}

Pour que le résolveur d’annonces puisse fonctionner, les fournisseurs d’annonces, tels que la prise de décision d’annonces Adobe Primetime, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.

TVSDK comprend la bibliothèque de prise de décision publicitaire Primetime. Pour que votre contenu comprenne des publicités provenant du serveur de prise de décision publicitaire Primetime, votre application doit fournir les `AuditudeSettings` informations &lt;a0/> requises suivantes :

* `mediaID`, qui est un identifiant unique pour la vidéo à lire.

   L’éditeur affecte l’ID de média lors de l’envoi de contenu vidéo et d’informations publicitaires au serveur de prise de décision publicitaire Adobe Primetime. Cet identifiant est utilisé par la prise de décision publicitaire Primetime pour récupérer les informations publicitaires associées à la vidéo sur le serveur.

* Votre `zoneID`, qui est attribué par Adobe, identifie votre société ou votre site Web.
* Domaine du serveur d’annonces affecté.
* Autres paramètres de ciblage.

   Vous pouvez inclure ces paramètres en fonction de vos besoins et des besoins du fournisseur d’annonces.

## Configurer les métadonnées d&#39;insertion de publicité {#set-up-ad-insertion-metadata}

Utilisez la classe d’assistance AuditudeSettings, qui étend la classe MetadataNode, pour configurer les métadonnées de prise de décision des publicités Adobe Primetime.

>[!TIP]
>
>La prise de décision publicitaire Adobe Primetime était auparavant connue sous le nom d’Auditude.

Les métadonnées publicitaires se trouvent dans la propriété `MediaResource.metadata`. Lors du démarrage de la lecture d’une nouvelle vidéo, votre application est chargée de définir les métadonnées publicitaires appropriées.

1. Créez l&#39;instance `AuditudeSettings`.

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings();
   ```

1. Définissez les paramètres de ciblage facultatifs MediaID, zoneID, domain et Adobe Primetime pour la prise de décision publicitaire.

   ```
   auditudeSettings.zoneId = "yourZoneID"; 
   auditudeSettings.mediaId = "media_identifier"; 
   auditudeSettings.domain = "yourAuditudeDomain"; 
   var targetingInfo:Metadata = new Metadata(); 
   targetingInfo.setValue("yourParamName", "yourParamValue"); 
   auditudeSettings.targetingInfo = targetingInfo;
   ```

   >[!TIP]
   >
   >L’ID de média est utilisé par TVSDK sous la forme d’une chaîne, convertie en valeur md5, et est utilisé pour la valeur `u` dans la demande d’URL de prise de décision et de Primetime. Par exemple :
   >
   >
   >` https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Créez une instance `MediaResource` en utilisant l’URL du flux média et les métadonnées publicitaires créées précédemment.

   ```
   var mediaResourceMetadata:MetadataNode = new MetadataNode(); 
   mediaResourceMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY, auditudeSettings); 
   var mediaResource:MediaResource = new MediaResource( 
         "www.example.com/video/test.m3u8", 
         MediaResourceType.HLS,  
         mediaResourceMetadata);
   ```

1. Chargez l&#39;objet `MediaResource` par l&#39;intermédiaire de la méthode `MediaPlayer.replaceCurrentResource`.

   Le `MediaPlayer` début le chargement et le traitement du manifeste de flux média.

1. (Facultatif) Requête l’instance `MediaPlayerItem` pour déterminer si le flux est actif, qu’il comporte des pistes audio de remplacement ou qu’il soit protégé.

   Ces informations peuvent vous aider à préparer l’interface utilisateur à la lecture. Par exemple, si vous savez qu&#39;il y a deux pistes audio, vous pouvez inclure une commande d&#39;interface utilisateur qui bascule entre ces pistes.

1. Appelez `MediaPlayer.prepareToPlay` pour début du processus publicitaire.

   Une fois les publicités résolues et placées dans la chronologie, `MediaPlayer` transition à l’état PRÉPARÉ.
1. Appelez `MediaPlayer.play` pour début de la lecture.

TVSDK comprend désormais des publicités lorsque votre média est lu.