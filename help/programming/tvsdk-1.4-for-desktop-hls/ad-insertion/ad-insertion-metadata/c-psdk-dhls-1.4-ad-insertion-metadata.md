---
description: Pour que le résolveur de publicités fonctionne, les fournisseurs de publicités, comme Adobe Primetime et la prise de décision, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
title: Métadonnées d’insertion publicitaire
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Métadonnées d’insertion publicitaire {#ad-insertion-metadata}

Pour que le résolveur de publicités fonctionne, les fournisseurs de publicités, comme Adobe Primetime et la prise de décision, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.

TVSDK comprend la bibliothèque de prise de décision publicitaire Primetime. Pour que votre contenu inclue de la publicité provenant du serveur de prise de décision publicitaire Primetime, votre application doit fournir les éléments suivants : `AuditudeSettings` information :

* `mediaID`, qui est un identifiant unique de la vidéo à lire.

  L’éditeur affecte l’identifiant mediaID lors de l’envoi de contenu vidéo et d’informations publicitaires au serveur de prise de décision publicitaire Adobe Primetime. Cet identifiant est utilisé par Primetime ad Decisioning pour récupérer les informations publicitaires associées pour la vidéo du serveur.

* Votre `zoneID`, qui est attribué par Adobe, identifie votre société ou votre site web.
* Domaine du serveur de publicités affecté.
* Autres paramètres de ciblage.

  Vous pouvez inclure ces paramètres en fonction de vos besoins et des besoins du fournisseur d’annonces publicitaires.

## Configuration des métadonnées d’insertion de publicités {#set-up-ad-insertion-metadata}

Utilisez la classe d’assistance AuditudeSettings , qui étend la classe MetadataNode , pour configurer les métadonnées de prise de décision publicitaire Adobe Primetime.

>[!TIP]
>
>La prise de décision publicitaire Adobe Primetime était auparavant connue sous le nom d’Auditude.

Les métadonnées publicitaires se trouvent dans la variable `MediaResource.metadata` . Lorsque vous démarrez la lecture d’une nouvelle vidéo, votre application est chargée de définir les métadonnées publicitaires correctes.

1. Créez la variable `AuditudeSettings` instance.

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings();
   ```

1. Définissez les paramètres de ciblage facultatifs MediaID, zoneID, domaine et Adobe Primetime Ad Decisioning.

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
   >L’identifiant du média est utilisé par TVSDK sous forme de chaîne, converti en valeur md5 et utilisé pour la variable `u` dans la requête d’URL de prise de décision publicitaire Primetime. Par exemple :
   >
   >
   >` https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Créez un `MediaResource` en utilisant l’URL du flux multimédia et les métadonnées publicitaires créées précédemment.

   ```
   var mediaResourceMetadata:MetadataNode = new MetadataNode(); 
   mediaResourceMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY, auditudeSettings); 
   var mediaResource:MediaResource = new MediaResource( 
         "www.example.com/video/test.m3u8", 
         MediaResourceType.HLS,  
         mediaResourceMetadata);
   ```

1. Chargez la variable `MediaResource` via l’objet `MediaPlayer.replaceCurrentResource` .

   La variable `MediaPlayer` démarre le chargement et le traitement du manifeste de flux multimédia.

1. (Facultatif) Interrogez le `MediaPlayerItem` pour voir si la diffusion est active, qu’elle dispose de pistes audio alternatives ou si la diffusion est protégée.

   Ces informations peuvent vous aider à préparer l’interface utilisateur pour la lecture. Par exemple, si vous savez qu’il existe deux pistes audio, vous pouvez inclure une commande de l’interface utilisateur qui bascule entre ces pistes.

1. Appeler `MediaPlayer.prepareToPlay` pour démarrer le workflow publicitaire.

   Une fois les publicités résolues et placées dans la chronologie, la variable `MediaPlayer` passe à l’état PRÉPARÉ .
1. Appeler `MediaPlayer.play` pour démarrer la lecture.

TVSDK comprend désormais des publicités lorsque votre média est lu.
