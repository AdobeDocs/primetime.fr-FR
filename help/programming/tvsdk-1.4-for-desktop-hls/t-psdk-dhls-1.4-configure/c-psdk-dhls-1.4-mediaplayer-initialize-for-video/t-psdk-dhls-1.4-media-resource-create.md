---
description: La classe MediaResource représente le contenu à charger par l'instance MediaPlayer.
seo-description: La classe MediaResource représente le contenu à charger par l'instance MediaPlayer.
seo-title: Création d’une ressource multimédia
title: Création d’une ressource multimédia
uuid: 3d03d92f-69b3-4da8-9b16-25a264115ae5
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Création d’une ressource multimédia {#create-a-media-resource}

Pour chaque nouveau contenu vidéo, initialisez une instance MediaResource avec des informations sur le contenu vidéo et chargez la ressource multimédia.

La classe MediaResource représente le contenu à charger par l&#39;instance MediaPlayer.

1. Créez un `MediaResource` en transmettant des informations sur le support au `MediaResource` constructeur.

   <table id="table_DD0D5D9129D54F73881399B9B4FF546A"> 
    <thead> 
      <tr> 
      <th colname="col1" class="entry"> Paramètre de constructeur </th> 
      <th colname="col2" class="entry"> Description </th> 
      </tr>
    </thead>
    =<tbody> 
      <tr> 
      <td colname="col1"><span class="codeph"> url</span> </td> 
      <td colname="col2"> <p>Chaîne représentant l’URL du manifeste/de la liste de lecture du média. </p> </td> 
      </tr> 
      <tr> 
      <td colname="col1"><span class="codeph"> type</span> </td> 
      <td colname="col2"> <p>L’une des valeurs de chaîne suivantes correspond au type de fichier indiqué : 
        <ul id="ul_7512E90B7B294EF9BFBA2D68DE678CBB"> 
        <li id="li_AA84434E84184A3D909552794B425ABD"><span class="codeph"> MP4</span> - Format de fichier multimédia de base ISO (MP4) </li> 
        <li id="li_8A2F3752569344B59EE30303A8393488"><span class="codeph"> HLS</span> - M3U8 </li> 
        </ul> </p> </td> 
      </tr> 
      <tr> 
      <td colname="col1"><span class="codeph"> metadata</span> </td> 
      <td colname="col2"> <p>Instance de la classe <span class="codeph"> Metadata</span> , qui peut contenir des informations personnalisées sur le contenu à charger. </p> <p>Par exemple, le contenu alternatif ou publicitaire à placer dans le contenu principal. Si vous utilisez la publicité, configurez <span class="codeph"> AuditudeSettings</span> avant d’utiliser ce constructeur. Pour plus d’informations, voir Métadonnées <a href="../../../tvsdk-1.4-for-desktop-hls/ad-insertion/ad-insertion-metadata/c-psdk-dhls-1.4-ad-insertion-metadata.md" format="dita" scope="local"> d’insertion</a>d’annonce. </p> </td> 
      </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >TVSDK ne prend en charge la lecture que pour des types de contenu spécifiques. Si vous tentez de charger un autre type de contenu, TVSDK distribue un événement d’erreur.
   >
   >Pour le contenu vidéo à la demande (VOD) MP4, TVSDK ne prend pas en charge les jeux vidéo, la diffusion en flux continu (ABR) adaptatif (adaptive bit rate), l’insertion de publicités, les sous-titres fermés ou la gestion des droits numériques.

   Le code suivant crée une `MediaResource` instance :

   ```
   // To do: Create metadata here
   MyResource = new MediaResource(
            "https://www.example.com/video/some-video.m3u8", 
            "HLS",
            MyMetadata)
   ```

   >[!TIP]
   >
   >A ce stade, vous pouvez utiliser `MediaResource` des accesseurs (getters) pour examiner le type, l’URL et les métadonnées de la ressource.

1. Chargez la ressource multimédia en utilisant l&#39;une des méthodes suivantes :

   * Votre instance MediaPlayer.

      Pour plus d’informations, voir [Chargement d’une ressource multimédia dans Media Player](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-mediaplayer-initialize-for-video/t-psdk-dhls-1.4-media-resource-load.md).
   * R `MediaPlayerItemLoader` Pour plus d’informations, voir [Chargement d’une ressource multimédia dans Media Player](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-mediaplayer-initialize-for-video/t-psdk-dhls-1.4-media-resource-load.md).

