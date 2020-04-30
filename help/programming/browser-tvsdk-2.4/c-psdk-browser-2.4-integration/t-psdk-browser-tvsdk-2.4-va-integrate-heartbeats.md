---
description: Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.
seo-description: Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.
seo-title: Initialisation et configuration des analyses vidéo
title: Initialisation et configuration des analyses vidéo
uuid: 4a582b35-ae92-4557-806d-e174fc878cc5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Initialisation et configuration des analyses vidéo {#initialize-and-configure-video-analytics}

Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.

Avant d’activer le suivi vidéo (pulsations vidéo), assurez-vous que vous disposez des éléments suivants :

* Configuration /Browser TVSDK Initialization Information - Contactez votre représentant Adobe pour obtenir des informations spécifiques sur votre compte de suivi vidéo :

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84">
 <tbody>
  <tr>
   <td colname="col1"> Point de terminaison du serveur de suivi AppMeasurement </td>
   <td colname="col2"> URL du point de terminaison de la collection principale d’Adobe Analytics (anciennement SiteCatalyst). </td>
  </tr>
  <tr>
   <td colname="col1"> Point de terminaison du serveur de suivi des analyses vidéo </td>
   <td colname="col2"> URL du point de terminaison de la collection principale d’analyses vidéo. C’est ici que sont envoyés tous les appels de suivi de pulsation vidéo. <p>Conseil :  L’URL du serveur de suivi du visiteur est identique à celle du serveur de suivi d’analyse. Pour plus d’informations sur la mise en oeuvre du service d’ID de Visiteur, voir <a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-target.html" format="html" scope="external"> Mise en oeuvre du service d’ID </a>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"> Nom du compte </td>
   <td colname="col2"> Connu également sous le nom d’identifiant de suite de rapports (RSID). </td>
  </tr>
  <tr>
   <td colname="col1"> ID d’organisation Marketing Cloud </td>
   <td colname="col2"> Valeur de chaîne requise pour instancier le composant Visiteur. </td>
  </tr>
  <tr>
   <td colname="col1"> Point de terminaison du serveur de suivi Visiteur </td>
   <td colname="col2"> URL du point de terminaison principal qui fournit un identifiant unique pour la visionneuse de vidéos active. </td>
  </tr>
  <tr>
   <td colname="col1"> Editeur </td>
   <td colname="col2"> Il s’agit de l’identifiant d’éditeur, qui est fourni aux clients par leur représentant Adobe. <p>Conseil :  Cet identifiant n'est pas simplement une chaîne portant le nom de la marque/de la télévision. </p> </td>
  </tr>
 </tbody>
</table>

Pour configurer le suivi vidéo dans votre lecteur :

1. Instanciez et configurez la bibliothèque VisitorAPI.

       Gardez à l’esprit les informations suivantes :
   
   * L’instanciation nécessite un paramètre d’entrée d’ID d’organisation Marketing Cloud fourni par Adobe.

      Il s’agit d’une valeur de chaîne.
   * La seule option de configuration pour la bibliothèque VisitorAPI est l’URL du point de terminaison principal qui fournit l’identifiant unique de l’utilisateur actuel.
   * L’URL du serveur de suivi du visiteur est identique à celle du serveur de suivi d’analyse.

      Pour plus d’informations sur la mise en oeuvre du service d’ID de Visiteur, voir Mise en oeuvre [du service d’ID de](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-target.html)Visiteur.

   ```js
   var_visitor = new Visitor("MARKETING_CLOUD_ORG_ID");
   _visitor.trackingServer = "URL_OF_THE_VISITOR_TRACKER_SERVER”;
   ```

2. Instanciez et configurez le composant AppMeasurement.

   L’instance AppMeasurement dispose de nombreuses options de configuration. Pour plus d’informations, consultez la documentation destinée aux développeurs [](https://microsite.omniture.com/t2/help/en_US/reference/#Developer) Adobe Analytics. Les options de l’exemple de code suivant ( `account`, `visitorNamespace`et `trackingServer`) sont requises et les valeurs sont fournies par Adobe.

   >[!IMPORTANT]
   >
   >Vous devez vous assurer que la chaîne de dépendance est correctement configurée. L’instance AppMeasurement agrégat (dépend) le composant API Visiteur.

   ```js
   var appMeasurement = new AppMeasurement();
   appMeasurement.visitor = visitor;
   appMeasurement.trackingServer = 'URL_OF_THE_ADOBE_ANALYTICS_TRACKING_SERVER';
   appMeasurement.account = 'ACCOUNT_NAME'; // Also known as RSID
   appMeasurement.pageName = 'Sample Page Name';
   appMeasurement.charSet = "UTF-8";
   appMeasurement.visitorID = "test-vid";
   ```

   >[!IMPORTANT]
   >
   >Dans votre application, veillez à ce que `appMeasurementObject.visitor` soit renseigné avant de lancer le flux d’analyses vidéo ou à ce que vous n’obteniez aucun résultat de suivi. Ces résultats sont indiqués par les messages de votre journal. Vous pouvez ajouter un appel de suivi vide ( `appMeasurementObject.track`), interroger la `visitor` propriété jusqu’à ce qu’elle soit renseignée et lancer l’analyse vidéo.

3. Initialisez et configurez les métadonnées de suivi de pulsation vidéo.

   >[!IMPORTANT]
   >
   >Vous pouvez arrêter le module d’analyse des vidéos en cours d’utilisation et le réinitialiser si nécessaire. Avant de réinitialiser le module, veillez à ce que les métadonnées des analyses vidéo soient également mises à jour afin d’obtenir les métadonnées de contenu appropriées. Pour recréer les métadonnées, répétez les étapes 1 et 2.

   1. Créez une instance des métadonnées d’analyses vidéo.
Cette instance contient toutes les informations de configuration nécessaires pour activer le suivi de pulsation vidéo. Par exemple :

      ```js
      function getVideoAnalyticsMetadata() {
          var vaObj = new AdobePSDK.VA.VideoAnalyticsMetadata();
          vaObj.appMeasurement = appMeasurement;
          vaObj.trackingServer = 'hbTrackingServer';
          vaObj.publisher = 'hbPublisher';
          vaObj.channel = 'sample-channel';
          vaObj.playerName = 'TVSDK-HTML';
          vaObj.appVersion = '1.0.0';
          vaObj.videoName = 'hbFriendlyName'; // this will overwrite the ContextData variable a.media.friendlyName
          vaObj.assetDuration = durationInSeconds;
          // use this to override the default asset length of -1 for live streams
          vaObj.debugLogging = false;
          return vaObj;
      }
      ```

   2. Après avoir créé une instance de lecteur multimédia, créez une instance de suivi Analyses vidéo et fournissez une référence à l’instance de lecteur multimédia.
Souvenez-vous des points suivants :

      * Créez toujours une instance de suivi pour chaque session de lecture de contenu et supprimez la référence précédente (après avoir détaché l’instance du lecteur multimédia).
      * Les métadonnées créées à la sous-étape 1 doivent être fournies dans le constructeur de l’outil de suivi des analyses vidéo.

         ```js
         var videoAnalyticsMetadata = getVideoAnalyticsMetadata();
         videoAnalyticsProvider = new AdobePSDK.VA.VideoAnalyticsProvider(videoAnalyticsMetadata);
         videoAnalyticsProvider.attachMediaPlayer(player);
         ```
   3. Détruisez l’outil de suivi des analyses vidéo.
Avant de commencer une nouvelle session de lecture de contenu, détruisez l’instance précédente du suivi vidéo. Une fois que vous avez reçu le événement (ou la notification) de fin de contenu, patientez quelques minutes avant de détruire l’instance du suivi vidéo. La suppression immédiate de l’instance peut affecter la capacité du suivi des analyses vidéo à envoyer un ping de fin de vidéo.

      ```js
      if (videoAnalyticsProvider) {
          videoAnalyticsProvider.detachMediaPlayer();
          videoAnalyticsProvider = null;
      ```
   4. Marquez manuellement le flux en direct/linéaire comme étant terminé.
Si vous avez plusieurs épisodes sur un flux en direct, vous pouvez marquer manuellement un épisode comme terminé en utilisant l’API complète. Ceci met fin à la session de suivi vidéo pour l’épisode vidéo en cours et vous pouvez en début une nouvelle pour l’épisode suivant.
      >[!TIP]
      >
      >Cette API est facultative et n’est pas nécessaire pour le suivi vidéo VOD.

      ```js
      if (videoAnalyticsProvider)
      {
         videoAnalyticsProvider.trackVideoComplete();
      videoAnalyticsProvider.detachMediaPlayer();
      videoAnalyticsProvider = null;
      // Create a new instance of VideoAnalyticsProvider to continue tracking.
      } 
      ```
