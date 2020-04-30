---
description: La classe MediaResource représente le contenu à charger par l'instance MediaPlayer.
seo-description: La classe MediaResource représente le contenu à charger par l'instance MediaPlayer.
seo-title: Création d’une ressource multimédia
title: Création d’une ressource multimédia
uuid: 9ae86c04-7bbe-43fb-9f57-1d9fa2fa73d0
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

---


# Création d’une ressource multimédia {#create-a-media-resource}

Pour chaque nouveau contenu vidéo, initialisez une instance MediaResource avec des informations sur le contenu vidéo et chargez la ressource multimédia.

La classe MediaResource représente le contenu à charger par l&#39;instance MediaPlayer.

1. Créez un `MediaResource` en transmettant des informations sur le support au `MediaResource` constructeur.

   Le `MediaResource` constructeur requiert les paramètres suivants :

   <table id="table_22886D6770FB45E99D35D0B90E6CC302"> 
   <thead> 
   <tr> 
      <th colname="col1" class="entry"> Paramètre de constructeur </th> 
      <th colname="col2" class="entry"> Description </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col1"> <span class="codeph"> url </span> </td> 
      <td colname="col2"> Chaîne représentant l’URL du manifeste/liste de lecture du média. </td> 
   </tr> 
   <tr> 
      <td colname="col1"> <span class="codeph"> type </span> </td> 
      <td colname="col2"> L’un des membres suivants de l’ <span class="codeph"> énumération </span> MediaResource.Type, correspondant au type de fichier indiqué : 
      <ul id="ul_C286ED3C31364B858A1C9AF3356E9282"> 
      <li id="li_25B24EF76D8849DE8764539F25E435FA"> <span class="codeph"> HLS </span> - M3U8 </li> 
      <li id="li_1344A41B434D49229E392F1AAF9ECA81"> <span class="codeph"> ISOBMFF </span> - Format de fichier de support de base ISO (MP4) </li> 
      <li id="li_92392073B7334916B06B16570C51AC91"> <span class="codeph"> DASH </span> - Description de la présentation multimédia MPEG-DASH (MPD) </li> 
      </ul> </td> 
   </tr> 
   <tr> 
      <td colname="col1"> <span class="codeph"> metadata </span> </td> 
      <td colname="col2"> Une instance de la <span class="codeph"> classe de </span> métadonnées (structure de type dictionnaire), qui peut contenir des informations supplémentaires sur le contenu sur le point d’être chargé, telles que le contenu alternatif ou publicitaire à placer dans le contenu principal. Si vous utilisez la publicité, configurez <span class="codeph"> les Paramètres d’Auditude </span> avant d’utiliser ce constructeur (voir href=Métadonnées d’insertion d’annonce](../../android-3.5-pub/insertion d’annonce/métadonnées d’insertion d’annonce/android-3.5-insertion-d’annonce-métadonnées.md). </td> 
   </tr> 
   </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >TVSDK ne prend en charge la lecture que pour des types de contenu spécifiques. Si vous tentez de charger un autre type de contenu, TVSDK distribue un événement d’erreur.
   >
   >Pour le contenu vidéo à la demande (VOD) MP4, TVSDK ne prend pas en charge les jeux vidéo, la diffusion en flux continu (ABR) adaptatif (adaptive bit rate), l’insertion de publicités, les sous-titres fermés ou la gestion des droits numériques.

   Le code suivant crée une `MediaResource` instance :        >

   ```java
   // To do: Create metadata here 
   MediaResource res = new MediaResource( 
     "https://www.example.com/video/some-video.m3u8",  
   MediaResource.Type.HLS, 
     metadata); 
   ```

   A tout moment après cette étape, vous pouvez utiliser `MediaResource` des accesseurs (getters) pour examiner le type, l’URL et les métadonnées de la ressource.

1. Chargez la ressource multimédia à l’aide de l’une des options suivantes :

   * Instance MediaPlayer.
   * `MediaPlayerItemLoader` Pour plus d’informations, voir [Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md).
   >[!IMPORTANT]
   >
   >Ne chargez pas la ressource multimédia sur un thread en arrière-plan. La plupart des opérations TVSDK doivent s’exécuter sur le thread principal et les exécuter sur un thread en arrière-plan peut provoquer une erreur et une fermeture.
