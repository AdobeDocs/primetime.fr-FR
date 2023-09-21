---
description: La classe MediaResource représente le contenu à charger par l’instance MediaPlayer.
title: Création d’une ressource multimédia
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Création d’une ressource multimédia {#create-a-media-resource}

Pour chaque nouveau contenu vidéo, initialisez une instance MediaResource avec des informations sur le contenu vidéo et chargez la ressource multimédia.

La classe MediaResource représente le contenu à charger par l’instance MediaPlayer.

1. Créez un `MediaResource` en transmettant des informations sur le média à la `MediaResource` constructeur.

   La variable `MediaResource` constructeur requiert les paramètres suivants :

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
      <td colname="col2"> L’un des membres suivants du groupe <span class="codeph"> MediaResource.Type </span> enum, correspondant au type de fichier indiqué :
      <ul id="ul_C286ED3C31364B858A1C9AF3356E9282">
      <li id="li_25B24EF76D8849DE8764539F25E435FA"> <span class="codeph"> HLS </span> - M3U8 </li>
      <li id="li_1344A41B434D49229E392F1AAF9ECA81"> <span class="codeph"> ISOBMFF </span> - Format de fichier multimédia de base ISO (MP4) </li>
      <li id="li_92392073B7334916B06B16570C51AC91"> <span class="codeph"> DASH </span> - Description de la présentation multimédia MPEG-DASH (MPD) </li>
      </ul> </td>
      </tr>
      <tr>
      <td colname="col1"> <span class="codeph"> metadata </span> </td>
      <td colname="col2"> Une instance de la fonction <span class="codeph"> Métadonnées </span> (structure de type dictionnaire), qui peut contenir des informations supplémentaires sur le contenu sur le point d’être chargé, telles que le contenu alternatif ou publicitaire à placer dans le contenu principal. Si vous utilisez la publicité, configurez <span class="codeph"> AuditudeSettings </span> avant d’utiliser ce constructeur. </td>
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
   // To do: Create metadata here
   MediaResource res = new MediaResource(
     "https://www.example.com/video/some-video.m3u8",
     MediaResource.Type.HLS,
     metadata);
   ```

   À tout moment après cette étape, vous pouvez utiliser `MediaResource` accesseurs (getters) pour examiner le type, l’URL et les métadonnées de la ressource.

1. Chargez la ressource multimédia à l’aide de l’une des options suivantes :

   * L’instance MediaPlayer.
   * `MediaPlayerItemLoader` Pour plus d’informations, voir [Chargement d’une ressource multimédia à l’aide de MediaPlayerItemLoader](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md).

   >[!IMPORTANT]
   >
   >Ne chargez pas la ressource multimédia sur un thread d’arrière-plan. La plupart des opérations TVSDK doivent s’exécuter sur le thread principal, et les exécuter sur un thread d’arrière-plan peut entraîner une erreur et une fermeture de l’opération.
