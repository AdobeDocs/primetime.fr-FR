---
description: Vous pouvez utiliser Adobe Offline Packager pour préparer le contenu de l’une des solutions DRM prises en charge par Primetime Cloud DRM, optimisée par ExpressPlay.
seo-description: Vous pouvez utiliser Adobe Offline Packager pour préparer le contenu de l’une des solutions DRM prises en charge par Primetime Cloud DRM, optimisée par ExpressPlay.
seo-title: Primetime Packager / Cloud DRM / TVSDK
title: Primetime Packager / Cloud DRM / TVSDK
uuid: e54a0e4d-c8ea-46d4-b1b0-bed8a680f8f5
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# Primetime Packager / Cloud DRM / TVSDK {#primetime-packager-cloud-drm-tvsdk}

Vous pouvez utiliser Adobe Offline Packager pour préparer le contenu de l’une des solutions DRM prises en charge par Primetime Cloud DRM, optimisée par ExpressPlay.

Cet ensemble d’instructions suppose que vous avez déjà configuré un compte d’administrateur ExpressPlay : [début rapide DRM Cloud Primetime](../../../multi-drm-workflows/quick-start/quick-overview.md).
1. Choisissez l’infrastructure à utiliser pour la création de packs de contenu. Primetime Packager prend en charge les packages de contenu en ligne de commande et basés sur la configuration pour une utilisation avec les DRM FairPlay, Widevine et PlayReady. Les formats et le chiffrement suivants sont actuellement pris en charge dans TVSDK (et d’autres sont en cours d’élaboration) :

   * DASH (CENC) / PlayReady, Widevine - Pour HTML5
   * HLS / FairPlay, Access - Pour iOS

1. Choisissez un système de gestion des clés (KMS) :

   * Utilisez le KMS d&#39;ExpressPlay ( [Enregistrement de clé ExpressPlay](https://www.expressplay.com/developer/key-storage/)); ce système gère vos clés de contenu via l’API RESTful d’ExpressPlay.

      ou...

   * Installez votre propre KMS. Créez une base de données de clés de contenu pouvant être sélectionnée par Content-ID.

      Dans les deux cas, le KMS gère un approvisionnement de clés de contenu, chaque clé étant associée à un ID de contenu.

1. Empaquetez votre contenu. Avec Primetime Packager, vous pouvez assembler un élément de contenu pour une solution DRM spécifique ou pour plusieurs solutions DRM.

   Les exemples de commandes suivants montrent des exemples de mise en package de contenu pour différentes solutions DRM :

   * [Widevine avec Primetime Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=19)  (génère un fichier MPD) :

      ```
      java -jar OfflinePackager.jar \ 
        -in_path [ 
        <your_content.mp4>] \ 
        -out_type dash \ 
        -out_path [ 
        <your_out_file_path>] \ 
        -drm \ 
        -drm_sys WIDEVINE \ 
        -key_file_path "creds/widevine_key.bin" \ 
        -widevine_key_id [ 
        <some_keyID>] \ 
        -widevine_content_id [ 
        <some_content-ID] \ 
        -widevine_header provider:intertrust#content_id:2a
      ```

   * [FairPlay avec Primetime Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=20)  (génère un fichier M3U8) :

      ```
      java -jar OfflinePackager.jar  
        -in_path [ 
        <your_content.mp4>]  
        -out_type hls  
        -out_path [ 
        <your_out_file_path>]  
        -drm  
        -drm_sys FAIRPLAY  
        -key_file_path "creds/fairplay_key.bin"  
        -key_url "user_provided_value"
      ```

      >[!NOTE]
      >
      >La valeur `key_url` est copiée telle quelle dans le fichier M3U8.

1. Créez un &quot;serveur de stockage&quot;.

       Le serveur de stockage doit gérer les opérations suivantes :
   
   1. Sélection du contenu par le client. Cette implémentation doit inclure un point de terminaison permettant aux clients de demander un jeton de contenu pour un ID de contenu spécifique.
   1. Droits du client
   1. Demandes de jeton de licence (ExpressPlay) du client ( [Demande de jeton de licence ExpressPlay / référence de réponse](../../../multi-drm-workflows/license-token-req-resp-ref/license-req-resp-overview.md))

1. Créez votre client.

       Le client doit inclure un appel à votre serveur de stockage. L’Adobe recommande au client d’appeler la vitrine une fois que l’utilisateur a sélectionné du contenu et une fois l’utilisateur authentifié. Ensuite, transmettez le jeton renvoyé d’ExpressPlay à votre lecteur pour l’utiliser pour les demandes de licence. Vous trouverez ci-dessous des informations sur la mise en oeuvre du composant DRM de vos lecteurs :
   
   * [Kit de développement TVSDK du navigateur pour HTML5](https://help.adobe.com/en_US/primetime/psdk/browser_tvsdk/index.html#PSDKs-reference-DRM_interface_overview)
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. Avec le jeton de licence en main, le client peut maintenant dériver l’URL de demande du jeton et demander la licence à ExpressPlay, puis lire le contenu sélectionné pour l’utilisateur.
