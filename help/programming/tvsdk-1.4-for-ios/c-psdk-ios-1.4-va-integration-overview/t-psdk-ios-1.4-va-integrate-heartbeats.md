---
description: Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.
seo-description: Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.
seo-title: Initialisation et configuration des analyses vidéo
title: Initialisation et configuration des analyses vidéo
uuid: 99c65d0b-ec3b-4a93-8dae-ef612112e510
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---


# Initialisation et configuration des analyses vidéo{#initialize-and-configure-video-analytics}

Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.

Avant d’activer le suivi vidéo (pulsations vidéo), assurez-vous que vous disposez des éléments suivants :

* TVSDK pour iOS
* Informations sur la configuration / l’initialisation - Contactez votre représentant d’Adobe pour obtenir des informations spécifiques sur votre compte de suivi vidéo :

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json  </span> </td> 
   <td colname="col2"> <p>Important :  Ce nom de fichier de configuration JSON doit rester <span class="codeph"> ADBMobileConfig.json </span>. Impossible de modifier le nom et le chemin d'accès de ce fichier de configuration. Le chemin d’accès à ce fichier doit être <span class="codeph"> &lt;racine source&gt;/AdobeMobile </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> Point de terminaison du serveur de  </span> suivi AppMeasurement </td> 
   <td colname="col2"> URL du point de terminaison de la collection principale Adobe Analytics (anciennement SiteCatalyst). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Point de terminaison du serveur de suivi des analyses vidéo </td> 
   <td colname="col2"> URL du point de terminaison de la collection principale d’analyses vidéo. C’est ici que sont envoyés tous les appels de suivi de pulsation vidéo. <p>Conseil :  L’URL du serveur de suivi du visiteur est identique à celle du serveur de suivi d’analyse. Pour plus d’informations sur l’implémentation du service d’ID de Visiteur, voir <a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-target.html" format="html" scope="external"> Mise en oeuvre du service d’ID </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Nom du compte </td> 
   <td colname="col2"> Connu également sous le nom d’identifiant de suite de rapports (RSID). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ID d'organisation Marketing Cloud </td> 
   <td colname="col2"> Valeur de chaîne requise pour instancier le composant Visiteur. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Editeur </td> 
   <td colname="col2"> Il s’agit de l’identifiant d’éditeur, fourni aux clients par leur représentant d’Adobe. <p>Conseil :  Cet identifiant n'est pas simplement une chaîne portant le nom de la marque/de la télévision. </p> </td> 
  </tr> 
 </tbody> 
</table>

Pour configurer le suivi vidéo dans votre lecteur :

1. Vérifiez que les options de temps de chargement du fichier de ressources `ADBMobileConfig.json` sont correctes.

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

   1. Vérifiez que le fichier `ADBMobileConfig.json` contient les valeurs appropriées fournies par l’Adobe.
   1. Vérifiez que ce fichier se trouve dans le dossier `AdobeMobile`.

      Ce dossier doit se trouver à la racine de l&#39;arborescence de la source de l&#39;application.
   1. Compilez et générez votre application.
   1. Déployez et exécutez l’application assemblée.

      Pour plus d’informations sur ces paramètres AppMeasurement, voir [Mesure vidéo en Adobe Analytics](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/video/).
1. Initialisez et configurez les métadonnées de suivi de pulsation vidéo.

   >[!IMPORTANT]
   >
   >Vous pouvez arrêter le module d’analyse des vidéos en cours d’utilisation et le réinitialiser si nécessaire. Avant de réinitialiser le module, veillez à ce que les métadonnées des analyses vidéo soient également mises à jour afin d’obtenir les métadonnées de contenu appropriées. Pour recréer les métadonnées, répétez les étapes 1 et 2.

   1. Créez une instance des métadonnées d’analyses vidéo.

      Cette instance contient toutes les informations de configuration nécessaires pour activer le suivi de pulsation vidéo. Par exemple :

      ```
      - (PTVideoAnalyticsTrackingMetadata *)getVideoAnalyticsTrackingMetadata 
      { 
          PTVideoAnalyticsTrackingMetadata *vaTrackingMetadata =  
            [[[PTVideoAnalyticsTrackingMetadata alloc]  
                 initWithTrackingServer:@"example.com" 
                 publisher:@"sample-publisher"] autorelease]; 
      
          // Set these to NO for production deployment. 
          vaTrackingMetadata.debugLogging = YES;  
          vaTrackingMetadata.quietMode = NO; 
      
          vaTrackingMetadata.channel = @"test-channel"; 
          vaTrackingMetadata.videoName = @"myvideo"; 
          vaTrackingMetadata.videoId = @"myvideoid"; 
          vaTrackingMetadata.playerName = @"PSDK Player"; 
          vaTrackingMetadata.enableChapterTracking = YES; 
          vaTrackingMetadata.useSSL = NO; 
          // use this API to override the default asset length -1 for live streams 
          vaTrackingMetadata.assetDuration = SAMPLE_ASSET_DURATION; 
      
      }
      ```

   1. Ajoutez les métadonnées Analyses vidéo à l’instance de métadonnées globale.

      Lorsque vous êtes prêt, définissez l’instance de métadonnées globale sur la ressource média ou l’élément du lecteur multimédia :

      ```
      - (PTMetadata *)createMetadata 
      { 
          PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
      
          [metadata setMetadata:[self getVideoAnalyticsTrackingMetadata]  
            forKey:PTVideoAnalyticsTrackingMetadataKey]; 
      
          return metadata; 
      } 
      
      PTMetadata *metadata = [self createMetadata]; 
      
      PTMediaPlayerItem *item =  
        [[[PTMediaPlayerItem alloc] initWithUrl:[[[NSURL alloc]  
          initWithString:@"media-url"] autorelease] 
          mediaId:@"media-id" metadata:metadata] autorelease];
      ```

   1. Initialisez le suivi des analyses vidéo.

      Après avoir créé une instance du lecteur de médias, vous devez créer une instance du suivi des analyses vidéo et fournir une référence à l’instance du lecteur de médias.

      >[!TIP]
      >
      >Créez toujours une instance d’outil de suivi pour chaque session de lecture de contenu et supprimez la référence précédente après avoir détaché l’instance du lecteur de médias.

      ```
      self.videoAnalyticsTracker =  
        [[[PTVideoAnalyticsTracker alloc] initWithMediaPlayer:self.player] autorelease];
      ```

   1. Détruisez l’outil de suivi des analyses vidéo.

      Avant de commencer une nouvelle session de lecture de contenu, détruisez l’instance précédente du suivi vidéo. Une fois que vous avez reçu le événement (ou la notification) de fin de contenu, patientez quelques minutes avant de détruire l’instance du suivi vidéo. La suppression immédiate de l’instance peut affecter la capacité du suivi des analyses vidéo à envoyer un ping de fin de vidéo.

      ```
      self.videoAnalyticsTracker = nil;
      ```

   1. Marquez manuellement le flux en direct/linéaire comme étant terminé.

      Si vous avez plusieurs épisodes sur un flux en direct, vous pouvez marquer manuellement un épisode comme terminé en utilisant l’API complète. Ceci met fin à la session de suivi vidéo pour l’épisode vidéo en cours et vous pouvez en début une nouvelle pour l’épisode suivant.

      >[!TIP]
      >
      >Cette API est facultative et n’est pas nécessaire pour le suivi vidéo VOD.

      ```
      if (self.videoAnalyticsTracker) 
      { 
         [self.videoAnalyticsTracker trackVideoComplete];   
      }
      ```

