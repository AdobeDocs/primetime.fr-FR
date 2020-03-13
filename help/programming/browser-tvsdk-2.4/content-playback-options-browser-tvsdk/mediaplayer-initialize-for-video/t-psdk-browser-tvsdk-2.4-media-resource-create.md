---
description: La classe MediaResource représente le contenu à charger par l’instance MediaPlayer.
seo-description: La classe MediaResource représente le contenu à charger par l’instance MediaPlayer.
seo-title: Création d’une ressource multimédia
title: Création d’une ressource multimédia
uuid: c25c037e-e9a0-430c-a150-b75a9ac051b1
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Création d’une ressource multimédia {#create-a-media-resource}

La classe MediaResource représente le contenu à charger par l’instance MediaPlayer.

1. Créez un `MediaResource` en transmettant des informations sur le support au `MediaResource` constructeur.

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
    <td colname="col2"> <p>L’un des membres suivants du <span class="codeph"> MediaResource.Type </span> qui correspond au type de fichier indiqué : </p> <p> 
    <ul id="ul_E9689FA06DC94BF4848F16E1F2F01A59"> 
    <li id="li_83A14B96CDC648C6AF6F5FA745343E1F"> <span class="codeph"> MP4 </span> - Format de fichier multimédia de base ISO (MP4) </li> 
    <li id="li_FCD355151515412D9A78C3815DD09129"> <span class="codeph"> HLS </span> - M3U8 </li> 
    <li id="li_9D3D306D49264830AC6EFB1F49524A3B"> <span class="codeph"> DASH </span> - MPD </li> 
    </ul> </p> <p></p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>métadonnées </p> </td> 
    <td colname="col2"> <p>Instance de la <span class="codeph"> classe </span> Metadata, qui peut contenir des informations personnalisées sur le contenu à charger. Par exemple, le contenu alternatif ou publicitaire à placer dans le contenu principal. Si vous utilisez la publicité, configurez <span class="codeph"> Paramètres d’audience </span> avant d’utiliser ce constructeur. Pour plus d’informations, voir <a href="../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md">Ad-insertion-metadata</a>. </p> <p>Conseil :  Vous pouvez forcer la reprise Flash, si nécessaire, en utilisant le paramètre <span class="codeph"> forceFlash </span> lors de la création d’une ressource multimédia. Cela peut s’avérer utile car, pour l’instant, toutes les fonctionnalités (telles que les  de publicité en direct) ne sont pas prises en charge dans le SDK du navigateur. La méthode de secours Flash est utilisée pour lire le contenu vidéo. </p> </td> 
    </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >Le SDK du navigateur prend en charge la lecture pour des types de contenu spécifiques uniquement. Si vous tentez de charger un autre type de contenu, le navigateur TVSDK distribue un  d’erreur.

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
   >A tout moment après, vous pouvez utiliser `MediaResource` des accesseurs (getters) pour examiner le type, l’URL et les métadonnées de la ressource.

1. Chargez votre instance MediaPlayer. Pour plus d’informations, voir [Chargement d’une ressource multimédia dans MediaPlayer](../../content-playback-options-browser-tvsdk/mediaplayer-initialize-for-video/t-psdk-browser-tvsdk-2.4-media-resource-load.md).
