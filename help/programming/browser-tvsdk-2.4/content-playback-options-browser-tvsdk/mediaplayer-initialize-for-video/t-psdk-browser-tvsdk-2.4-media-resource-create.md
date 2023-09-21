---
description: La classe MediaResource représente le contenu à charger par l’instance MediaPlayer.
title: Création d’une ressource multimédia
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Création d’une ressource multimédia {#create-a-media-resource}

La classe MediaResource représente le contenu à charger par l’instance MediaPlayer.

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
    <td colname="col2"> <p>L’un des membres suivants du groupe <span class="codeph"> MediaResource.Type </span> énumération correspondant au type de fichier indiqué : </p> <p> 
    <ul id="ul_E9689FA06DC94BF4848F16E1F2F01A59"> 
    <li id="li_83A14B96CDC648C6AF6F5FA745343E1F"> <span class="codeph"> MP4 </span> - Format de fichier multimédia de base ISO (MP4) </li> 
    <li id="li_FCD355151515412D9A78C3815DD09129"> <span class="codeph"> HLS </span> - M3U8 </li> 
    <li id="li_9D3D306D49264830AC6EFB1F49524A3B"> <span class="codeph"> DASH </span> - MPD </li> 
    </ul> </p> <p></p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>metadata </p> </td> 
    <td colname="col2"> <p>Une instance de la fonction <span class="codeph"> Métadonnées </span> qui peut contenir des informations personnalisées sur le contenu à charger. Par exemple, le contenu alternatif ou publicitaire à placer dans le contenu principal. Si vous utilisez la publicité, configurez <span class="codeph"> AuditudeSettings </span> avant d’utiliser ce constructeur. Pour plus d’informations, voir <a href="../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md">Ad-insertion-metadata</a>. </p> <p>Conseil : Vous pouvez forcer le Flash de secours, si nécessaire, en utilisant la variable <span class="codeph"> forceFlash </span> lors de la création d’une ressource multimédia. Cela peut s’avérer utile, car actuellement, toutes les fonctionnalités (telles que les workflows de publicité en direct) ne sont pas prises en charge dans le SDK du navigateur. Le Flash de secours est utilisé pour lire le contenu vidéo. </p> </td> 
    </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >Le TVSDK du navigateur prend en charge la lecture pour des types de contenu spécifiques uniquement. Si vous tentez de charger un autre type de contenu, le navigateur TVSDK distribue un événement d’erreur.

   Le code suivant crée une `MediaResource` instance :

   ```js
   //create a MediaResource instance pointing to some HLS content 
   Metadata metadata = //TODO: create metadata here 
   mediaResource = new AdobePSDK.MediaResource ( 
         "https://www.example.com/video/some-video.m3u8", 
         AdobePSDK.MediaResourceType.HLS,  
         metadata);
   ```

   >[!TIP]
   >
   >À tout moment après cela, vous pouvez utiliser `MediaResource` accesseurs (getters) pour examiner le type, l’URL et les métadonnées de la ressource.

1. Chargez votre instance MediaPlayer. Pour plus d’informations, voir [Chargement d’une ressource multimédia dans MediaPlayer](../../content-playback-options-browser-tvsdk/mediaplayer-initialize-for-video/t-psdk-browser-tvsdk-2.4-media-resource-load.md).
