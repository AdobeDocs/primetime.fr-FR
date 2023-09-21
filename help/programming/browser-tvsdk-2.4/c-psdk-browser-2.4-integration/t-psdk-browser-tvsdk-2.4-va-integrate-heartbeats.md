---
description: Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.
title: Initialisation et configuration des analyses vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 0%

---

# Initialisation et configuration des analyses vidéo {#initialize-and-configure-video-analytics}

Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.

Avant d’activer le suivi vidéo (pulsations vidéo), vérifiez que vous disposez des éléments suivants :

* Configuration /Browser TVSDK Informations sur l’initialisation - Contactez votre représentant d’Adobe pour obtenir des informations spécifiques sur votre compte de suivi vidéo :

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84">
 <tbody>
  <tr>
   <td colname="col1"> Point d’entrée du serveur de suivi des AppMeasurements </td>
   <td colname="col2"> URL du point de terminaison de la collection principale Adobe Analytics (anciennement SiteCatalyst). </td>
  </tr>
  <tr>
   <td colname="col1"> Point d’entrée du serveur de suivi Video Analytics </td>
   <td colname="col2"> URL du point de terminaison de la collection principale d’analyse vidéo. C’est là que tous les appels de suivi de pulsation vidéo sont envoyés. <p>Conseil : L’URL du serveur de suivi des visiteurs est identique à celle du serveur de suivi des analyses. Pour plus d’informations sur l’implémentation du service d’identification des visiteurs, voir <a href="https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-target.html?lang=en" format="html" scope="external"> Mise en oeuvre du service d’ID </a>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"> Nom du compte </td>
   <td colname="col2"> Également appelé identifiant de suite de rapports (RSID). </td>
  </tr>
  <tr>
   <td colname="col1"> ID d’organisation de Marketing Cloud </td>
   <td colname="col2"> Valeur string requise pour instancier le composant Visiteur. </td>
  </tr>
  <tr>
   <td colname="col1"> Point d’entrée du serveur de suivi des visiteurs </td>
   <td colname="col2"> URL du point de terminaison principal qui fournit un identifiant unique pour la visionneuse de vidéos actuelle. </td>
  </tr>
  <tr>
   <td colname="col1"> Éditeur </td>
   <td colname="col2"> Il s’agit de l’identifiant d’éditeur, fourni aux clients par leur représentant d’Adobe. <p>Conseil : Cet identifiant n’est pas seulement une chaîne portant le nom de la marque/de la télévision. </p> </td>
  </tr>
 </tbody>
</table>

Pour configurer le suivi vidéo dans votre lecteur :

1. Instanciez et configurez la bibliothèque VisitorAPI .

       Gardez les informations suivantes à l’esprit :
   
   * L’instanciation nécessite un paramètre d’entrée ID d’organisation de Marketing Cloud fourni par Adobe.

     Il s’agit d’une valeur string .
   * La seule option de configuration de la bibliothèque VisitorAPI est l’URL du point de terminaison principal qui fournit l’identifiant unique de l’utilisateur actuel.
   * L’URL du serveur de suivi des visiteurs est identique à celle du serveur de suivi des analyses.

     Pour plus d’informations sur l’implémentation du service d’identification des visiteurs, voir [Mise en oeuvre du service d’identification des visiteurs](https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-target.html?lang=en).

   ```js
   var_visitor = new Visitor("MARKETING_CLOUD_ORG_ID");
   _visitor.trackingServer = "URL_OF_THE_VISITOR_TRACKER_SERVER”;
   ```

2. Instanciez et configurez le composant AppMeasurement.

   L’instance d’AppMeasurement comporte de nombreuses options de configuration. Pour plus d’informations, voir [Développeur Adobe Analytics](https://microsite.omniture.com/t2/help/en_US/reference/#Developer) la documentation. Les options de l’exemple de code suivant ( `account`, `visitorNamespace`, et `trackingServer`) sont obligatoires et les valeurs sont fournies par Adobe.

   >[!IMPORTANT]
   >
   >Vous devez vous assurer que la chaîne de dépendance est correctement configurée. L’instance d’AppMeasurement agrège (dépend) le composant API visiteur.

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
   >Dans votre application, assurez-vous que `appMeasurementObject.visitor` est renseignée avant de lancer le flux d’analyse vidéo, ou vous risquez de ne pas obtenir de résultats de suivi. Ces résultats sont indiqués par les messages de votre journal. Vous pouvez ajouter un appel de suivi vide ( `appMeasurementObject.track`), interroge la variable `visitor` jusqu’à ce qu’elle soit renseignée, puis lancez video analytics.

3. Initialisez et configurez les métadonnées de suivi de pulsation vidéo.

   >[!IMPORTANT]
   >
   >Vous pouvez arrêter le module d’analyse vidéo en cours et le réinitialiser à nouveau, si nécessaire. Avant de réinitialiser le module, assurez-vous que les métadonnées d’analyse vidéo sont également mises à jour vers les métadonnées de contenu correctes. Pour recréer les métadonnées, répétez les sous-étapes 1 et 2.

   1. Créez une instance des métadonnées Video Analytics.
Cette instance contient toutes les informations de configuration nécessaires pour activer le suivi de pulsation vidéo. Par exemple :

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

   2. Après avoir créé une instance de lecteur multimédia, créez une instance de suivi Video Analytics et fournissez une référence à l’instance du lecteur multimédia.
Gardez à l’esprit les éléments suivants :

      * Créez toujours une instance de suivi pour chaque session de lecture de contenu, puis supprimez la référence précédente (après avoir désolidarisé l’instance du lecteur multimédia).
      * Les métadonnées créées à la sous-étape 1 doivent être fournies dans le constructeur de Video Analytics Tracker.

        ```js
        var videoAnalyticsMetadata = getVideoAnalyticsMetadata();
        videoAnalyticsProvider = new AdobePSDK.VA.VideoAnalyticsProvider(videoAnalyticsMetadata);
        videoAnalyticsProvider.attachMediaPlayer(player);
        ```

   3. Détruisez le suivi Video Analytics.
Avant de commencer une nouvelle session de lecture de contenu, détruisez l’instance précédente du dispositif de suivi vidéo. Une fois que vous avez reçu l’événement de fin de contenu (ou la notification), attendez quelques minutes avant de détruire l’instance de suivi vidéo. La suppression immédiate de l’instance peut affecter la capacité du dispositif de suivi Video Analytics à envoyer un ping de fin vidéo.

      ```js
      if (videoAnalyticsProvider) {
          videoAnalyticsProvider.detachMediaPlayer();
          videoAnalyticsProvider = null;
      ```

   4. Marque manuellement la diffusion en direct/linéaire comme étant terminée.
Si vous avez plusieurs épisodes sur un flux en direct, vous pouvez marquer manuellement un épisode comme terminé à l’aide de l’API complète. Cela met fin à la session de suivi vidéo de l’épisode vidéo en cours et vous pouvez commencer une nouvelle session de suivi de l’épisode suivant.
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
