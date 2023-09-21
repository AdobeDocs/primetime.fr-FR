---
description: Vous pouvez utiliser le module hors ligne d’Adobe pour préparer le contenu pour l’une des solutions DRM prises en charge par Primetime Cloud DRM, optimisée par ExpressPlay.
title: Primetime Packager/Cloud DRM/TVSDK
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Primetime Packager/Cloud DRM/TVSDK {#primetime-packager-cloud-drm-tvsdk}

Vous pouvez utiliser le module hors ligne d’Adobe pour préparer le contenu pour l’une des solutions DRM prises en charge par Primetime Cloud DRM, optimisée par ExpressPlay.

Cet ensemble d’instructions suppose que vous avez déjà configuré un compte administrateur ExpressPlay : [Quick Start Primetime DRM Cloud](../../../multi-drm-workflows/quick-start/quick-overview.md).
1. Choisissez l&#39;infrastructure à utiliser pour créer un package de votre contenu. Primetime Packager prend en charge les packages de contenu basés sur la ligne de commande et la configuration pour une utilisation avec les DRM FairPlay, Widevine et PlayReady. Les formats et le chiffrement suivants sont actuellement pris en charge dans TVSDK (avec d’autres formats dans le pipeline) :

   * DASH (CENC) / PlayReady, Widevine - For HTML5
   * HLS / FairPlay, Accès - Pour iOS

1. Choisissez un système de gestion des clés (KMS) :

   * Utilisez le KMS d’ExpressPlay ( [Stockage clé ExpressPlay](https://www.expressplay.com/developer/key-storage/)) ; ce système gère vos clés de contenu par le biais de l’API RESTful de ExpressPlay.

     ou ...

   * Installez votre propre KMS. Créez une base de données de clés de contenu pouvant être sélectionnée par l’identifiant de contenu.

     Dans les deux cas, le KMS gère un ensemble de clés de contenu, chaque clé étant associée à un ID de contenu.

1. Regroupez votre contenu. Avec Primetime Packager, vous pouvez regrouper un élément de contenu pour une solution DRM spécifique ou pour plusieurs solutions DRM.

   Les exemples de commandes suivants présentent des exemples de regroupement de contenu pour différentes solutions DRM :

   * [Widevine avec Primetime Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=19) (génère le fichier MPD) :

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

   * [FairPlay avec Primetime Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=20) (Génère un fichier M3U8) :

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
     >La variable `key_url` est copiée telle quelle dans le fichier M3U8.

1. Créez un &quot;serveur storefront&quot;.

       Le serveur storefront doit gérer les opérations suivantes :
   
   1. Sélection du contenu par le client. Cette implémentation doit inclure un point de terminaison pour que les clients puissent demander un jeton de contenu pour un identifiant de contenu spécifique.
   1. Droits des clients
   1. Demandes de jeton de licence (ExpressPlay) du client ( [Demande/référence de réponse de jeton de licence ExpressPlay](../../../multi-drm-workflows/license-token-req-resp-ref/license-req-resp-overview.md))

1. Créez votre client.

       Le client doit inclure un appel vers votre serveur de storefront. Adobe recommande que le client appelle le storefront une fois que l’utilisateur a sélectionné du contenu et une fois l’utilisateur authentifié. Ensuite, transmettez le jeton renvoyé par ExpressPlay à votre lecteur afin qu’il l’utilise pour les demandes de licence. Vous trouverez ci-dessous des informations sur la mise en oeuvre du composant DRM de vos lecteurs :
   
   * [Browser TVSDK pour HTML5](https://help.adobe.com/en_US/primetime/psdk/browser_tvsdk/index.html#PSDKs-reference-DRM_interface_overview)
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. Avec le jeton de licence en main, le client peut désormais extraire l’URL de demande du jeton et envoyer la demande de licence à ExpressPlay, puis lire le contenu sélectionné pour l’utilisateur.
