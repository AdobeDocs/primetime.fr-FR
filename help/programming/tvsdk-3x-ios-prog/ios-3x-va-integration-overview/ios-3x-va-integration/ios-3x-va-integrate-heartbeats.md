---
description: Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.
seo-description: Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.
seo-title: Initialisation et configuration des analyses vidéo
title: Initialisation et configuration des analyses vidéo
uuid: d1dc9425-e67c-4e13-aee7-302149352506
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Initialisation et configuration des analyses vidéo {#initialize-and-configure-video-analytics}

Vous pouvez configurer votre lecteur pour suivre et analyser l’utilisation de la vidéo.

Avant d’activer le suivi vidéo (pulsations vidéo), assurez-vous que vous disposez des éléments suivants :

* TVSDK pour iOS
* Informations sur la configuration / Initialisation - Contactez votre représentant Adobe pour obtenir des informations spécifiques sur votre compte de suivi vidéo :

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json </span> </td> 
   <td colname="col2"> <p>Important :  Ce nom de fichier de configuration JSON doit rester <span class="codeph"> ADBMobileConfig.json </span>. Le nom et le chemin d'accès de ce fichier de configuration ne peuvent pas être modifiés. Le chemin d’accès à ce fichier doit être <span class="codeph"> &lt;racine source&gt;/AdobeMobile </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> Point de terminaison du serveur de </span> suivi AppMeasurement </td> 
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
   <td colname="col1"> Editeur </td> 
   <td colname="col2"> Il s’agit de l’identifiant de l’éditeur, fourni aux clients par leur représentant Adobe. <p>Conseil :  Cet identifiant n'est pas seulement une chaîne portant le nom de la marque/de la télévision. </p> </td> 
  </tr> 
 </tbody> 
</table>

Pour configurer le suivi vidéo dans votre lecteur :

1. Vérifiez que les options de temps de chargement du fichier de `ADBMobileConfig.json` ressources sont correctes.

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

   Ce fichier de configuration au format JSON est assemblé en tant que ressource avec TVSDK. Votre lecteur lit ces valeurs uniquement au moment du chargement et les valeurs restent constantes pendant l’exécution de votre application.

   Pour configurer les options de temps de chargement :

   1. Vérifiez que le `ADBMobileConfig.json` fichier contient les valeurs appropriées fournies par Adobe.
   1. Vérifiez que ce fichier se trouve dans le `AdobeMobile` dossier.

      Ce dossier doit se trouver à la racine de l’arborescence de la source de l’application.
   1. Compilez et créez votre application.
   1. Déployez et exécutez l’application intégrée.

      Pour plus d’informations sur ces paramètres AppMeasurement, voir [Mesure vidéo dans Adobe Analytics](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/video/).
1. Initialisez et configurez les métadonnées de suivi de pulsation vidéo.

   >[!IMPORTANT]
   >
   >Vous pouvez arrêter le module d’analyse vidéo en cours d’utilisation et le réinitialiser si nécessaire. Avant de réinitialiser le module, assurez-vous que les métadonnées des analyses vidéo sont également mises à jour vers les métadonnées de contenu correctes. Pour recréer les métadonnées, répétez les étapes 1 et 2.

   1. Créez une instance des métadonnées Analytics vidéo.

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

   1. Ajouter les métadonnées Analytics vidéo à l’instance de métadonnées globale.

      Lorsque vous êtes prêt, définissez l’instance de métadonnées globale sur la ressource multimédia ou l’élément du lecteur multimédia :

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

      Après avoir créé une instance de lecteur multimédia, vous devez créer une instance de suivi d’analyses vidéo et fournir une référence à l’instance de lecteur multimédia.

      >[!TIP]
      >
      >Créez toujours une instance de suivi pour chaque session de lecture de contenu et supprimez la référence précédente après avoir détaché l’instance du lecteur multimédia.

      ```
      self.videoAnalyticsTracker =  
        [[[PTVideoAnalyticsTracker alloc] initWithMediaPlayer:self.player] autorelease];
      ```

   1. Détruisez le suivi des analyses vidéo.

      Avant de commencer une nouvelle session de lecture de contenu, détruisez l’instance précédente de l’outil de suivi vidéo. Une fois que vous avez reçu le  (ou la notification) du contenu terminé, attendez quelques minutes avant de détruire l’instance de suivi vidéo. La destruction immédiate de l’instance peut gêner la capacité du suivi des analyses vidéo à envoyer un ping de fin de vidéo.

      ```
      self.videoAnalyticsTracker = nil;
      ```

   1. Marquez manuellement le flux en direct/linéaire comme étant terminé.

      Si vous avez plusieurs épisodes sur un flux en direct, vous pouvez marquer manuellement un épisode comme terminé à l’aide de l’API complète. Cette opération met fin à la session de suivi vidéo pour l’épisode vidéo en cours et vous pouvez  une nouvelle session de suivi pour l’épisode suivant.

      >[!TIP]
      >
      >Cette API est facultative et n’est pas nécessaire pour le suivi vidéo VOD.

      ```
      if (self.videoAnalyticsTracker) 
      { 
         [self.videoAnalyticsTracker trackVideoComplete];   
      }
      ```
