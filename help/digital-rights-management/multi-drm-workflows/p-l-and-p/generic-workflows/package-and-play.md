---
description: Vous pouvez utiliser le gestionnaire de package Bento4 d’ExpressPlay pour préparer le contenu pour toutes les solutions DRM prises en charge par Primetime Cloud DRM, optimisé par ExpressPlay.
seo-description: Vous pouvez utiliser le gestionnaire de package Bento4 d’ExpressPlay pour préparer le contenu pour toutes les solutions DRM prises en charge par Primetime Cloud DRM, optimisé par ExpressPlay.
seo-title: ExpressPlay Packager / Cloud DRM / TVSDK
title: ExpressPlay Packager / Cloud DRM / TVSDK
uuid: 0d2f5a8d-15c4-42ba-acb8-1dc8d5bc62de
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# ExpressPlay Packager / Cloud DRM / TVSDK {#expressplay-packager-cloud-drm-tvsdk}

Vous pouvez utiliser le gestionnaire de package Bento4 d’ExpressPlay pour préparer le contenu pour toutes les solutions DRM prises en charge par Primetime Cloud DRM, optimisé par ExpressPlay.

Ce décrit comment utiliser un outil tiers pour préparer du contenu protégé, dans ce cas, *ExpressPlay Bento4 Tools*, pour une utilisation avec une variété de solutions DRM. Pour plus d&#39;informations, consultez la documentation des outils ** Bento4 sur le site Web [ExpressPlay](https://www.expressplay.com/developer/) .
1. Achetez un compte ExpressPlay et obtenez vos informations d’authentification du client ExpressPlay.

   Reportez-vous à la page [Primetime DRM Cloud Quick-.](../../quick-start/quick-overview.md)
1. Si vous chiffrez du contenu pour Primetime Access, achetez le SDK Primetime Adobe Access d’Adobe, ainsi que les certificats requis (certificat de licence, certificat de transport et certificat de création de package).
1. Fournissez une clé de chiffrement de contenu (CEK) et une clé de chiffrement de contenu  l’ID de (CEKSID) à utiliser sur les systèmes DRM. (Vous les générez de manière aléatoire à l’aide d’OpenSSL ou d’autres méthodes similaires.)

   Le CEK est la clé réelle que vous utilisez pour chiffrer vos fichiers vidéo. Soit vous le stockez en toute sécurité sur votre propre serveur dans votre propre système de gestion des clés, soit vous pouvez utiliser la solution [de clés ExpressPlay](https://www.expressplay.com/developer/key-storage/).

   Un CEKSID est l’identifiant d’un CEK particulier. Vous ne transmettez pas (habituellement) la clé de chiffrement. Par exemple, lorsque vous demandez un jeton de licence, vous fournissez le CEKSID.

1. Si vous chiffrez du contenu pour Access, utilisez votre CEK pour créer des métadonnées d’accès Primetime associées à votre contenu.

1. Fragmentez votre contenu pour le préparer pour l’outil *Bento4 MP4DASH* .

   Pour cette étape, vous pouvez utiliser l’outil *MP4FRAGMENT* . Vous n’avez besoin de fragmenter votre contenu qu’une seule fois. Par exemple :

   ```
   ./mp4fragment Unfragmented.mp4 Fragmented.mp4
   ```

1. Utilisez l&#39;outil *Bento4 MPDASH* pour &quot;DASH-ify&quot; et chiffrer votre contenu fragmenté.

   Utilisez cette commande pour spécifier tous les systèmes DRM que vous allez utiliser et transmettre les métadonnées d’accès Primetime générées à partir des étapes précédentes. Par exemple :

   ```
   /mp4dash -f  
   --use-segment-list  
   --use-segment-timeline  
   --encryption-key=<CEKSID>:<CEK>  
   --playready  
   --Widevine  
   --Widevine-header=provider:intertrust#content_id:2a  
   --primetime  
   --primetime-metadata=@AAXS.metadata 
    Fragmented.mp4 -o DASH_OUTPUT
   ```

1. Créez un &quot;serveur de stockage&quot;.

       Ce serveur doit gérer les opérations suivantes :
   
   1. Sélection du contenu par le client. Cette implémentation doit inclure un point de fin pour que les clients puissent demander un jeton de contenu pour un ID de contenu spécifique.
   1. Droits du client
   1. Demandes de jeton de licence (ExpressPlay) du client (demande de jeton de licence [ExpressPlay / référence](../../license-token-req-resp-ref/license-req-resp-overview.md)de réponse)

1. Créez votre client.

   Le client doit inclure un appel à votre serveur de stockage. Adobe conseille au client d’appeler la vitrine une fois que l’utilisateur a sélectionné du contenu et une fois l’utilisateur authentifié. Ensuite, transmettez le jeton renvoyé par ExpressPlay à votre lecteur pour l’utiliser pour les demandes de licence. Vous trouverez ici des informations sur la mise en oeuvre du composant DRM de vos lecteurs :

   * Navigateur TVSDK pour HTML5
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. Avec le jeton de licence en main, le client peut maintenant dériver l’URL de demande du jeton et faire la demande de licence vers ExpressPlay, puis lire le contenu protégé et sélectionné pour l’utilisateur.
