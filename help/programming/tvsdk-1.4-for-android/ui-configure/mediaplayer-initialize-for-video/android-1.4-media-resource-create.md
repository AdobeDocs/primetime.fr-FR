---
description: Pour chaque nouveau contenu vidéo, initialisez une instance MediaResource avec des informations sur le contenu vidéo et chargez la ressource multimédia. La classe MediaResource représente le contenu à charger par l’instance MediaPlayer.
title: Création d’une ressource multimédia
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Création d’une ressource multimédia {#create-a-media-resource}

Pour chaque nouveau contenu vidéo, initialisez une instance MediaResource avec des informations sur le contenu vidéo et chargez la ressource multimédia. La classe MediaResource représente le contenu à charger par l’instance MediaPlayer.

1. Créez un `MediaResource` en transmettant des informations sur le média à la `MediaResource` constructeur.

   <table id="table_DD0D5D9129D54F73881399B9B4FF546A"> 
    <thead> 
    <tr> 
    <th colname="col1" class="entry"> Paramètre du constructeur </th> 
    <th colname="col2" class="entry"> Description </th> 
    </tr> 
    </thead>
    <tbody> 
    <tr> 
    <td colname="col1"> <p>url </p> </td> 
    <td colname="col2"> <p>Chaîne représentant l’URL du manifeste/de la liste de lecture du média. </p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>type </p> </td> 
    <td colname="col2"> <p>L’un des membres suivants du groupe <span class="codeph"> MediaResource.Type </span> énumération correspondant au type de fichier indiqué : 
    <ul id="ul_72636C41CA7E4538A3BE11A79E0282FC"> 
    <li id="li_070960200DEB40E992C58FCB8909AEA3"> <span class="codeph"> HLS </span> - M3U8 </li> 
    </ul> </p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>metadata </p> </td> 
    <td colname="col2"> <p>Une instance de la fonction <span class="codeph"> Métadonnées </span> qui peut contenir des informations personnalisées sur le contenu à charger. </p> <p>Par exemple, le contenu alternatif ou publicitaire à placer dans le contenu principal. Si vous utilisez la publicité, configurez <span class="codeph"> AuditudeSettings </span>. Pour plus d’informations, voir <a href="../../../tvsdk-1.4-for-android/ad-insertion/ad-insertion-metadata/android-1.4-ad-insertion-metadata-set-up.md" format="dita" scope="local"> Métadonnées Ad Insertion </a>. </p> </td> 
    </tr> 
    </tbody> 
    </table>

   >[!IMPORTANT]
   >
   >TVSDK ne prend en charge la lecture que pour des types de contenu spécifiques. Si vous tentez de charger un autre type de contenu, TVSDK distribue un événement d’erreur.
   >
   >Pour le contenu vidéo à la demande (VOD) MP4, TVSDK ne prend pas en charge les fonctions de lecture, de diffusion en continu à débit adaptatif (ABR), d’insertion de publicités, de sous-titres fermés ou DRM.

   Le code suivant crée une `MediaResource` instance :

   ```java
   try { 
       // create a MediaResource instance pointing to some HLS content 
       Metadata metadata = //TODO: create metadata  
       MediaResource mediaResource = MediaResource.createFromUrl( 
         "https://www.example.com/video/some-video.m3u8",  
         MediaResource.Type.HLS,  
         metadata); 
   } catch(IllegalArgumentException ex) { 
       // this exception is thrown if the URL does not point  
       // to a valid url. 
   } 
   ```

   >[!TIP]
   >
   >À ce stade, vous pouvez utiliser `MediaResource` accesseurs (getters) pour examiner le type, l’URL et les métadonnées de la ressource.

1. Chargez la ressource multimédia à l’aide des éléments suivants :

   * Votre instance MediaPlayer.

     Pour plus d’informations, voir [Chargement d’une ressource multimédia dans MediaPlayer](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-resource-load.md).
   * A `MediaPlayerItemLoader` Pour plus d’informations, voir [Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md).

   >[!IMPORTANT]
   >
   >Ne chargez pas la ressource multimédia sur un thread d’arrière-plan. La plupart des opérations TVSDK doivent être exécutées sur le thread principal, et les exécuter sur un thread d’arrière-plan peut entraîner une erreur et une fermeture de l’opération.
