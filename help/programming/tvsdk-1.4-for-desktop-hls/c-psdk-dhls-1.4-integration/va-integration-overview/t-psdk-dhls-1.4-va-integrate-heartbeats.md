---
description: Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.
seo-description: Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.
seo-title: Initialisation et configuration des analyses vidéo
title: Initialisation et configuration des analyses vidéo
uuid: ece5ddc1-3f7b-4878-b1bc-1fec0a459add
translation-type: tm+mt
source-git-commit: 6cb3463be8986d8a1dc718655bd929a0f07ac00d

---


# Initialisation et configuration des analyses vidéo{#initialize-and-configure-video-analytics}

Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.

Avant d’activer le suivi vidéo (pulsations vidéo), assurez-vous que vous disposez des éléments suivants :

* TVSDK pour HLS de bureau
* Informations sur la configuration / Initialisation - Contactez votre représentant Adobe pour obtenir des informations spécifiques sur votre compte de suivi vidéo :

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> Point de terminaison du serveur de suivi AppMeasurement </td> 
   <td colname="col2"> URL du point de terminaison de la collection principale d’Adobe Analytics (anciennement SiteCatalyst). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Point de terminaison du serveur de suivi vidéo </td> 
   <td colname="col2"> URL du point de terminaison de la collection principale d’analyses vidéo. C’est là que sont envoyés tous les appels de suivi de pulsation vidéo. <p>Conseil :  L’URL du serveur de suivi des est identique à celle du serveur de suivi des analyses. Pour plus d’informations sur la mise en oeuvre du service d’ID de, voir <a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-target.html" format="html" scope="external"> Mise en oeuvre du service d’ID </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Nom du compte </td> 
   <td colname="col2"> Egalement appelé ID de suite de rapports (RSID). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ID d’organisation Marketing Cloud </td> 
   <td colname="col2"> Valeur de chaîne requise pour l’instanciation du composant. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Point de terminaison du serveur de suivi </td> 
   <td colname="col2"> URL du point de fin principal qui fournit un identifiant unique pour la visionneuse de vidéos active. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Editeur </td> 
   <td colname="col2"> Il s’agit de l’identifiant de l’éditeur, fourni aux clients par leur représentant Adobe. <p>Conseil :  Cet identifiant n'est pas seulement une chaîne portant le nom de la marque/de la télévision. </p> </td> 
  </tr> 
 </tbody> 
</table>

Pour configurer le suivi vidéo dans votre lecteur :

1. Instanciez et configurez la bibliothèque VisitorAPI.

       Gardez à l’esprit les informations suivantes :
   
   * L’instanciation nécessite un paramètre d’entrée ID d’organisation Marketing Cloud fourni par Adobe.

      Il s’agit d’une valeur de chaîne.
   * La seule option de configuration pour la bibliothèque VisitorAPI est l’URL du point de fin principal qui fournit l’identifiant unique de l’utilisateur actuel.
   * L’URL du serveur de suivi des est identique à celle du serveur de suivi des analyses.

      Pour plus d’informations sur la mise en oeuvre du service d’ID de, voir Mise en oeuvre du service d’ID de.

   ```
   var_visitor = new Visitor("MARKETING_CLOUD_ORG_ID"); 
   _visitor.trackingServer = "URL_OF_THE_VISITOR_TRACKER_SERVER”; 
   ```

1. Instanciez et configurez le composant AppMeasurement.

   L’instance AppMeasurement comporte de nombreuses options de configuration. Pour plus d’informations, voir la documentation du développeur [](https://microsite.omniture.com/t2/help/en_US/reference/#Developer) Adobe Analytics. Les options de l’exemple de code suivant ( `account`, `visitorNamespace`et `trackingServer`) sont requises et les valeurs sont fournies par Adobe.

   >[!IMPORTANT]
   >
   >Vous devez vous assurer que la chaîne de dépendance est correctement configurée. L’instance AppMeasurement  l’ (dépend) du composant API du.

   ```
   // Instantiate and configure AppMeasurement 
   
   // Instantiate AppMeasurement instance only once! 
   if (_appMeasurementObject == null) {  
       _appMeasurementObject = new AppMeasurement(); 
   } 
   
   with (_appMeasurementObject) { 
       account = "ACCOUNT_NAME"; // Also known as RSID 
       trackingServer = "URL_OF_THE_ADOBE_ANALYTICS_TRACKING_SERVER"; 
   
       // Use the same value here as for the Visitor API component 
       visitorNamespace = "MARKETING_CLOUD_ORG_ID"; 
   
       // Attach the Visitor API to the AppMeasurement instance. 
       visitor = _visitor;  
       pageName = "pageName"; 
       charSet = "UTF-8"; 
       currencyCode = "USD"; 
   } 
   ```

   >[!IMPORTANT]
   >
   >Dans votre application, veillez à ce que `appMeasurementObject.visitor` soit renseigné avant de lancer le flux d’analyses vidéo, sinon vous n’obtiendrez peut-être aucun résultat de suivi. Ces résultats sont indiqués par les messages de votre journal. Vous pouvez ajouter un appel de suivi vide ( `appMeasurementObject.track`), interroger la `visitor` propriété jusqu’à ce qu’elle soit renseignée, puis lancer l’analyse vidéo.

1. Initialisez et configurez les métadonnées de suivi de pulsation vidéo.

   >[!IMPORTANT]
   >
   >Vous pouvez arrêter le module d’analyse vidéo en cours d’utilisation et le réinitialiser si nécessaire. Avant de réinitialiser le module, assurez-vous que les métadonnées des analyses vidéo sont également mises à jour vers les métadonnées de contenu correctes. Pour recréer les métadonnées, répétez les étapes 1 et 2.

   1. Créez une instance des métadonnées Analytics vidéo.

      Cette instance contient toutes les informations de configuration nécessaires pour activer le suivi de pulsation vidéo. Par exemple :

      ```
      private function getVideoAnalyticsTrackingMetadata():VideoAnalyticsMetadata {     
          // Initialize visitor id service and appMeasurement      
          [...] // as shown in the previous steps     
      
          var vaMetadata:VideoAnalyticsMetadata = new VideoAnalyticsMetadata(); 
      
          with (vaMetadata) { 
              trackingServer = "hbTrackingServer"; 
              publisher = "hbPublisher"; 
              channel = "hbChannel";  
              playerName = "hbPlayerName"; 
      
              // this overwrites the ContextData variable a.media.friendlyName 
              videoName = "hbFriendlyName";  
      
              // this will overwrite the ContextData variable a.media.name 
              videoId = "hbName"; 
      
              enableChapterTracking = true; 
      
              // Set these to false for production deployment 
              debugLogging = true;  
              quietMode = false; 
      
          } 
      } 
      ```

   1. Ajouter les métadonnées Analytics vidéo à l’instance de métadonnées globale.

      Lorsque vous êtes prêt, définissez l’instance de métadonnées globale sur la ressource multimédia ou l’élément du lecteur multimédia :

      ```
      var resourceMetadata:Metadata = _player.currentItem.resource.metadata; 
      resourceMetadata.setMetadata(DefaultMetadataKeys.VIDEO_ANALYTICS_METADATA_KEY,  
                                   getVideoAnalyticsTrackingMetadata());
      ```

   1. Initialisez le suivi des analyses vidéo.

      Après avoir créé une instance de lecteur multimédia, vous devez créer une instance de suivi d’analyses vidéo et fournir une référence à l’instance de lecteur multimédia.

      >[!TIP]
      >
      >Créez toujours une instance de suivi pour chaque session de lecture de contenu et supprimez la référence précédente après avoir détaché l’instance du lecteur multimédia.

      ```
      _videoAnalyticsProvider = new VideoAnalyticsProvider(_appMeasurementObject); 
      _videoAnalyticsProvider.attachMediaPlayer(_player);
      ```

   1. Détruisez le suivi des analyses vidéo.

      Avant de commencer une nouvelle session de lecture de contenu, détruisez l’instance précédente de l’outil de suivi vidéo. Une fois que vous avez reçu le  (ou la notification) du contenu terminé, attendez quelques minutes avant de détruire l’instance de suivi vidéo. La destruction immédiate de l’instance peut gêner la capacité du suivi des analyses vidéo à envoyer un ping de fin de vidéo.

      ```
      if (videoAnalyticsTracker) { 
          videoAnalyticsTracker.detachMediaPlayer(); 
          videoAnalyticsTracker = null; 
      }
      ```

   1. Marquez manuellement le flux en direct/linéaire comme étant terminé.

      Si vous avez plusieurs épisodes sur un flux en direct, vous pouvez marquer manuellement un épisode comme terminé à l’aide de l’API complète. Cette opération met fin à la session de suivi vidéo pour l’épisode vidéo en cours et vous pouvez  une nouvelle session de suivi pour l’épisode suivant.

      >[!TIP]
      >
      >Cette API est facultative et n’est pas nécessaire pour le suivi vidéo VOD.

