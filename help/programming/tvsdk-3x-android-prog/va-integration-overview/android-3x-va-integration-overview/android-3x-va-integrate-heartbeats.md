---
description: 'null'
seo-description: 'null'
seo-title: Initialisation et configuration des analyses vidéo
title: Initialisation et configuration des analyses vidéo
uuid: c49c77d9-66b9-4586-9d70-b139b4a97a7a
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Initialisation et configuration des analyses vidéo {#initialize-and-configure-video-analytics}

Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.
Avant d’activer le suivi vidéo (pulsations vidéo), assurez-vous que vous disposez des éléments suivants :

* TVSDK 3.0 pour Android.
* Informations sur la configuration / l’initialisation

   Contactez votre représentant Adobe pour obtenir des informations spécifiques sur votre compte de suivi vidéo :

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json </span> </td> 
   <td colname="col2"> <p>Important :  Ce nom de fichier de configuration JSON doit rester <span class="filepath"> ADBMobileConfig.json </span>. Impossible de modifier le nom et le chemin d'accès de ce fichier de configuration. Le chemin d’accès à ce fichier doit être <span class="filepath"> &lt;racine source&gt;/assets </span>. </p> </td> 
  </tr> 
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
 </tbody> 
</table>

Pour configurer le suivi vidéo dans votre lecteur :

1. Vérifiez que les options de temps de chargement du fichier de `ADBMobileConfig.json` ressources sont correctes.

       &quot;
     {
     &quot;version&quot; : &quot;1.1&quot;,
     &quot;analytics&quot; : {
     &quot;rsids&quot; : &quot;adobedevelopment&quot;,
     &quot;server&quot; : &quot;10.131.129.149:3000&quot;,
     &quot;charset&quot; : &quot;UTF-8&quot;,
     &quot;ssl&quot; : false,
     &quot;offlineEnabled&quot; : false,
     &quot;lifecycleTimeout&quot; : 5,
     &quot;batchLimit&quot; : 50,
     &quot;privacyDefault&quot; : &quot;optedin&quot;,
     &quot;poi&quot; : []
 },     
     &quot;marketingCloud&quot; : {
     &quot;org&quot; : &quot;VALEUR FOURNIE PAR ADOBE&quot;
     },
     &quot;cible&quot; : {
     &quot;clientCode&quot; : &quot;&quot;,
     &quot;timeout&quot; : 5
     },
     &quot;audienceManager&quot; : {
     &quot;server&quot; : &quot;
 &quot;     
 }     
 }     &quot;
  Ce fichier de configuration au format JSON est fourni en tant que ressource avec TVSDK.     
     Votre lecteur lit ces valeurs uniquement au moment du chargement et les valeurs restent constantes pendant l’exécution de votre application.
       
       Pour configurer les options de temps de chargement :
   
   1. Vérifiez que le `ADBMobileConfig.json` fichier contient les valeurs appropriées (fournies par Adobe).
   1. Vérifiez que ce fichier se trouve dans le `assets/` dossier.

      Ce dossier doit se trouver à la racine de l&#39;arborescence de la source de l&#39;application.

   1. Compilez et générez votre application.
   1. Déployez et exécutez l’application assemblée.

      Pour plus d’informations sur ces paramètres AppMeasurement, voir [Mesure vidéo dans Adobe Analytics](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/video/).

1. Initialisez et configurez les métadonnées de suivi de pulsation vidéo.

   >[!IMPORTANT]
   >
   >Vous pouvez arrêter le module d’analyse des vidéos en cours d’utilisation et le réinitialiser si nécessaire. Avant de réinitialiser le module, veillez à ce que les métadonnées des analyses vidéo soient également mises à jour afin d’obtenir les métadonnées de contenu appropriées. Pour recréer les métadonnées, répétez les deux premières étapes ci-dessous (sous-étapes **a** et **b**).

   1. Créez une instance des métadonnées d’analyses vidéo.

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

   1. Initialisez le fournisseur d’analyses vidéo.

      Après avoir créé une instance du lecteur multimédia, vous devez créer une instance du fournisseur d’analyses vidéo et lui fournir le contexte de l’application.

      >[!TIP]
      >
      >Créez toujours une instance de fournisseur pour chaque session de lecture de contenu et supprimez la référence précédente après avoir détaché l’instance du lecteur de médias.

      ```java
      VideoAnalyticsProvider videoAnalyticsProvider = new VideoAnalyticsProvider(appContext); 
      ```

   1. Définissez les métadonnées des analyses vidéo sur l’ `videoAnalyticsProvider` instance.

      ```java
      videoAnalyticsProvider.setVideoAnalyticsMetadata(vaMetadata);
      ```

   1. Joignez l’instance du lecteur multimédia à l’ `videoAnalyticsProvider` instance :

      ```java
      videoAnalyticsProvider.attachMediaPlayer(mediaPlayer); 
      ```

   1. Détruisez le fournisseur d’analyses vidéo.

      Avant de commencer une nouvelle session de lecture de contenu, détruisez l’instance précédente du fournisseur de vidéos. Une fois que vous avez reçu le événement (ou la notification) de fin de contenu, patientez quelques minutes avant de détruire l’instance du fournisseur d’analyses vidéo. La suppression immédiate de l’instance peut affecter la capacité du fournisseur d’analyses vidéo à envoyer un ping &quot;complete video&quot; (fin de la vidéo).

      ```java
      if (videoAnalyticsProvider) { 
          videoAnalyticsProvider.detachMediaPlayer(); 
          videoAnalyticsProvider = null; 
      }
      ```

   1. Marquez manuellement le flux en direct/linéaire comme étant terminé.

      Si vous avez plusieurs épisodes sur un flux en direct, vous pouvez marquer manuellement un épisode comme terminé en utilisant l’API complète. Ceci met fin à la session de suivi vidéo pour l’épisode vidéo en cours et vous pouvez en début une nouvelle pour l’épisode suivant.

      >[!TIP]
      >
      >Cette API est facultative et ne fonctionne pas pour le suivi vidéo VOD.

      ```java
      if (videoAnalyticsProvider) { 
          videoAnalyticsProvider.trackVideoComplete();    
      }
      ```
