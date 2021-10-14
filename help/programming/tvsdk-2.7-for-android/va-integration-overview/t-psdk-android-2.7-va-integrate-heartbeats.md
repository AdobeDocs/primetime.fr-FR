---
title: Initialisation et configuration des analyses vidéo
description: Initialisation et configuration des analyses vidéo
copied-description: true
exl-id: add832e3-5a17-4235-a76f-ae342e1d85f0
source-git-commit: 3bbf70e07b51585c9b53f470180d55aa7ac084bc
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# Initialisation et configuration des analyses vidéo {#initialize-and-configure-video-analytics}

Vous pouvez configurer votre lecteur pour effectuer le suivi et analyser l’utilisation de la vidéo.
Avant d’activer le suivi vidéo (pulsations vidéo), vérifiez que vous disposez des éléments suivants :

* TVSDK 2.5 pour Android.
* Informations sur la configuration/l’initialisation

   Contactez votre représentant d’Adobe pour obtenir des informations spécifiques sur votre compte de suivi vidéo :

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json  </span> </td> 
   <td colname="col2"> <p>Important :  Ce nom de fichier de configuration JSON doit rester <span class="filepath"> ADBMobileConfig.json </span>. Le nom et le chemin d’accès de ce fichier de configuration ne peuvent pas être modifiés. Le chemin d’accès à ce fichier doit être <span class="filepath"> &lt;racine source&gt;/assets </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Point d’entrée du serveur de suivi AppMeasurement </td> 
   <td colname="col2"> URL du point de terminaison de la collection principale Adobe Analytics (anciennement SiteCatalyst). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Point d’entrée du serveur de suivi Video Analytics </td> 
   <td colname="col2"> URL du point de terminaison de la collection principale d’analyse vidéo. C’est là que tous les appels de suivi de pulsation vidéo sont envoyés. <p>Conseil :  L’URL du serveur de suivi des visiteurs est identique à celle du serveur de suivi des analyses. Pour plus d’informations sur la mise en oeuvre du service d’identification des visiteurs, voir <a href="https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-target.html?lang=en" format="html" scope="external"> Mise en oeuvre du service d’identification </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Nom du compte </td> 
   <td colname="col2"> Également appelé identifiant de suite de rapports (RSID). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ID d’organisation de Marketing Cloud </td> 
   <td colname="col2"> Valeur string requise pour instancier le composant Visiteur. </td> 
  </tr> 
 </tbody> 
</table>

Pour configurer le suivi vidéo dans votre lecteur :

1. Vérifiez que les options de temps de chargement dans le fichier de ressources `ADBMobileConfig.json` sont correctes.

   ```
   { 
       "version" : "1.1", 
       "analytics" : { 
           "rsids" : "adobedevelopment", 
           "server" : "10.131.129.149:3000", 
           "charset" : "UTF-8", 
           "ssl" : false, 
           "offlineEnabled" : false, 
           "lifecycleTimeout" : 5, 
           "batchLimit" : 50, 
           "privacyDefault" : "optedin", 
           "poi" : [] 
       }, 
       "marketingCloud": { 
           "org": "ADOBE PROVIDED VALUE"  
       }, 
       "target" : { 
           "clientCode" : "", 
           "timeout" : 5 
       }, 
       "audienceManager" : { 
           "server" : "" 
       } 
   }
   ```

   Ce fichier de configuration au format JSON est fourni en tant que ressource avec TVSDK. Votre lecteur lit ces valeurs uniquement au moment du chargement et les valeurs restent constantes pendant l’exécution de votre application.

   Pour configurer les options de temps de chargement :


   1. Vérifiez que le fichier `ADBMobileConfig.json` contient les valeurs appropriées (fournies par Adobe).
   1. Vérifiez que ce fichier se trouve dans le dossier `assets/`.

      Ce dossier doit se trouver à la racine de l’arborescence de la source de votre application.

   1. Compilez et créez votre application.
   1. Déployez et exécutez l’application groupée.

      Pour plus d’informations sur ces paramètres AppMeasurement, voir [Mesure vidéo dans Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=en).

1. Initialisez et configurez les métadonnées de suivi de pulsation vidéo.

   >[!IMPORTANT]
   >
   >Vous pouvez arrêter le module d’analyse vidéo en cours et le réinitialiser à nouveau, si nécessaire. Avant de réinitialiser le module, assurez-vous que les métadonnées d’analyse vidéo sont également mises à jour vers les métadonnées de contenu correctes. Pour recréer les métadonnées, répétez les deux premières étapes ci-dessous (sous-étapes **a** et **b**).

   1. Créez une instance des métadonnées Video Analytics.

      Cette instance contient toutes les informations de configuration nécessaires pour activer le suivi de pulsation vidéo. Par exemple :

      ```java
      private VideoAnalyticsMetadata getVideoAnalyticsTrackingMetadata() { 
          VideoAnalyticsMetadata vaMetadata = new VideoAnalyticsMetadata(); 
      
          vaMetadata.setTrackingServer("example.com"); 
          vaMetadata.setChannel("test-channel"); 
          vaMetadata.setVideoName("myvideo"); 
          vaMetadata.setVideoId("myvideoid"); 
          vaMetadata.setPlayerName("PSDK Player"); 
          vaMetadata.setUseSSL(false); 
          vaMetadata.debugLogging = true; // Set to NO for production deployment. 
          vaMetadata.setEnableChapterTracking(true); 
          // use this API to override the default asset length -1 for live streams 
          vaMetadata.setAssetDuration(SAMPLE_ASSET_DURATION); 
      
          return vaMetadata; 
      }
      ```

   1. Initialisez le fournisseur Video Analytics.

      Après avoir créé une instance du lecteur multimédia, vous devez créer une instance du fournisseur Video Analytics et lui fournir le contexte de l’application.

      >[!TIP]
      >
      >Créez toujours une instance de fournisseur pour chaque session de lecture de contenu et supprimez la référence précédente après avoir désolidarisé l’instance du lecteur multimédia.

      ```java
      VideoAnalyticsProvider videoAnalyticsProvider = new VideoAnalyticsProvider(appContext); 
      ```

   1. Définissez les métadonnées Video Analytics sur l’instance `videoAnalyticsProvider`.

      ```java
      videoAnalyticsProvider.setVideoAnalyticsMetadata(vaMetadata);
      ```

   1. Joignez l’instance du lecteur multimédia à l’instance `videoAnalyticsProvider` :

      ```java
      videoAnalyticsProvider.attachMediaPlayer(mediaPlayer); 
      ```

   1. Détruisez le fournisseur Video Analytics.

      Avant de commencer une nouvelle session de lecture de contenu, détruisez l’instance précédente du fournisseur vidéo. Une fois que vous avez reçu l’événement de fin de contenu (ou la notification), attendez quelques minutes avant de détruire l’instance du fournisseur d’analyses vidéo. La suppression immédiate de l’instance peut interférer avec la capacité du fournisseur Video Analytics d’envoyer un ping &quot;video complete&quot;.

      ```java
      if (videoAnalyticsProvider) { 
          videoAnalyticsProvider.detachMediaPlayer(); 
          videoAnalyticsProvider = null; 
      }
      ```

   1. Marque manuellement la diffusion en direct/linéaire comme étant terminée.

      Si vous avez plusieurs épisodes sur un flux en direct, vous pouvez marquer manuellement un épisode comme terminé à l’aide de l’API complète. Cela met fin à la session de suivi vidéo de l’épisode vidéo en cours et vous pouvez commencer une nouvelle session de suivi de l’épisode suivant.

      >[!TIP]
      >
      >Cette API est facultative et ne fonctionne pas pour le suivi vidéo VOD.

      ```java
      if (videoAnalyticsProvider) { 
          videoAnalyticsProvider.trackVideoComplete();    
      }
      ```
