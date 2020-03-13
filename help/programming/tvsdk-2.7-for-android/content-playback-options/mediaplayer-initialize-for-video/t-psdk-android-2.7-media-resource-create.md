---
description: La classe MediaResource représente le contenu à charger par l’instance MediaPlayer.
seo-description: La classe MediaResource représente le contenu à charger par l’instance MediaPlayer.
seo-title: Création d’une ressource multimédia
title: Création d’une ressource multimédia
uuid: f34a11a3-dac2-405e-8632-1d9617cc019d
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# Création d’une ressource multimédia {#create-a-media-resource}

Pour chaque nouveau contenu vidéo, initialisez une instance MediaResource avec des informations sur le contenu vidéo et chargez la ressource multimédia.

La classe MediaResource représente le contenu à charger par l’instance MediaPlayer.

1. Créez un `MediaResource` en transmettant des informations sur le support au `MediaResource` constructeur.

   Le `MediaResource` constructeur requiert les paramètres suivants :

   <table id="table_22886D6770FB45E99D35D0B90E6CC302"> 
      <thead> 
      <tr> 
      <th colname="col1" class="entry"> Paramètre du constructeur </th> 
      <th colname="col2" class="entry"> Description </th> 
      </tr> 
      </thead>
      <tbody> 
      <tr> 
      <td colname="col1"> <span class="codeph"> url </span> </td> 
      <td colname="col2"> Chaîne représentant l’URL du manifeste/de la liste de lecture du média. </td> 
      </tr> 
      <tr> 
      <td colname="col1"> <span class="codeph"> type </span> </td> 
      <td colname="col2"> L’un des membres suivants de l’énumération <span class="codeph"> MediaResource.Type </span> , correspondant au type de fichier indiqué : 
      <ul id="ul_C286ED3C31364B858A1C9AF3356E9282"> 
      <li id="li_25B24EF76D8849DE8764539F25E435FA"> <span class="codeph"> HLS </span> - M3U8 </li> 
      <li id="li_1344A41B434D49229E392F1AAF9ECA81"> <span class="codeph"> ISOBMFF </span> - Format de fichier de support de base ISO (MP4) </li> 
      <li id="li_92392073B7334916B06B16570C51AC91"> <span class="codeph"> DASH </span> - Description de la présentation multimédia MPEG-DASH (MPD) </li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td colname="col1"> <span class="codeph"> métadonnées </span> </td> 
      <td colname="col2"> Une instance de la <span class="codeph"> classe </span> de métadonnées (une structure de type dictionnaire), qui peut contenir des informations supplémentaires sur le contenu qui est sur le point d’être chargé, telles que le contenu alternatif ou publicitaire à placer dans le contenu principal. Si vous utilisez la publicité, configurez <span class="codeph"> Paramètres d’audience </span> avant d’utiliser ce constructeur (voir <a keyref="ad-insertion-metadata"></a>). </td> 
      </tr> 
      </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >TVSDK ne prend en charge la lecture que pour des types de contenu spécifiques. Si vous tentez de charger un autre type de contenu, TVSDK distribue un  d’erreur.
   >
   >Pour le contenu vidéo à la demande (VOD) MP4, TVSDK ne prend pas en charge le flux de lecture par astuce, le débit binaire adaptatif (ABR) en flux continu, l’insertion de publicités, les sous-titres ou la gestion des droits numériques.

   Le code suivant crée une `MediaResource` instance :

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
   * `MediaPlayerItemLoader` Pour plus d’informations, voir [Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md).
   >[!IMPORTANT]
   >
   >Ne chargez pas la ressource multimédia sur un thread en arrière-plan. La plupart des opérations TVSDK doivent s’exécuter sur le thread principal, et les exécuter sur un thread d’arrière-plan peut entraîner une erreur et une fermeture.
