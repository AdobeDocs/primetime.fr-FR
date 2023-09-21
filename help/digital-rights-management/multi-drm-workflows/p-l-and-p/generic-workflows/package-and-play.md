---
description: Vous pouvez utiliser le package Bento4 d’ExpressPlay pour préparer le contenu pour l’une des solutions DRM prises en charge par Primetime Cloud DRM, optimisée par ExpressPlay.
title: ExpressPlay Packager/Cloud DRM/TVSDK
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# ExpressPlay Packager/Cloud DRM/TVSDK {#expressplay-packager-cloud-drm-tvsdk}

Vous pouvez utiliser le package Bento4 d’ExpressPlay pour préparer le contenu pour l’une des solutions DRM prises en charge par Primetime Cloud DRM, optimisée par ExpressPlay.

Cette tâche décrit comment utiliser un outil tiers pour préparer du contenu protégé, dans ce cas *Outils ExpressPlay Bento4*, à utiliser avec diverses solutions DRM. Pour plus d’informations, voir *Outils Bento4* la documentation relative à la [ExpressPlay](https://www.expressplay.com/developer/) site web.
1. Acquérez un compte ExpressPlay et obtenez vos informations sur l’authentificateur client ExpressPlay.

   Voir [Démarrage rapide de Primetime DRM Cloud.](../../quick-start/quick-overview.md)
1. Si vous chiffrez du contenu pour Primetime Access , achetez le SDK Primetime Adobe Access à partir d’Adobe, ainsi que les certificats requis (certificat de licence, de transport et de package).
1. Fournissez une clé de chiffrement de contenu (CEK) et un identifiant de stockage de clé de chiffrement de contenu (CEKSID) à utiliser sur les systèmes DRM. (Vous les générez de manière aléatoire à l’aide d’OpenSSL ou d’une méthode similaire.)

   Le CEK est la clé que vous utilisez pour chiffrer votre ou vos fichiers vidéo. Vous pouvez soit le stocker en toute sécurité sur votre propre serveur dans votre propre système de gestion des clés, soit utiliser les [solution de stockage clé](https://www.expressplay.com/developer/key-storage/).

   Un CEKSID est l’identifiant d’un CEK spécifique. Vous ne transmettez pas (généralement) la clé de chiffrement. Par exemple, lorsque vous demandez un jeton de licence, vous fournissez le CEKSID.

1. Si vous chiffrez du contenu pour Access, utilisez votre CEK pour créer des métadonnées Primetime Access associées à votre contenu.

1. Fragmentez votre contenu pour le préparer pour la *Bento4 MP4DASH* outil.

   Pour cette étape, vous pouvez utiliser la variable *MP4FRAGMENT* outil. Vous ne devez fragmenter votre contenu qu’une seule fois. Par exemple :

   ```
   ./mp4fragment Unfragmented.mp4 Fragmented.mp4
   ```

1. Utilisez la variable *Bento4 MPDASH* pour &quot;DASH-ify&quot; et chiffrer votre contenu fragmenté.

   Utilisez cette commande pour spécifier tous les systèmes DRM que vous utiliserez et transmettre toutes les métadonnées d’accès Primetime générées à partir des étapes précédentes. Par exemple :

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

1. Créez un &quot;serveur storefront&quot;.

       Ce serveur doit gérer les opérations suivantes :
   
   1. Sélection du contenu par le client. Cette implémentation doit inclure un point de terminaison pour que les clients puissent demander un jeton de contenu pour un identifiant de contenu spécifique.
   1. Droits des clients
   1. Demandes de jeton de licence (ExpressPlay) du client ( [Demande/référence de réponse de jeton de licence ExpressPlay](../../license-token-req-resp-ref/license-req-resp-overview.md))

1. Créez votre client.

   Le client doit inclure un appel vers votre serveur de storefront. Adobe recommande que le client appelle le storefront une fois que l’utilisateur a sélectionné du contenu et une fois l’utilisateur authentifié. Ensuite, transmettez le jeton renvoyé par ExpressPlay à votre lecteur afin qu’il l’utilise pour les demandes de licence. Vous trouverez ci-dessous des informations sur la mise en oeuvre du composant DRM de vos lecteurs :

   * Browser TVSDK pour HTML5
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. Avec le jeton de licence en main, le client peut désormais extraire l’URL de demande du jeton et envoyer la demande de licence à ExpressPlay, puis lire le contenu sélectionné et protégé pour l’utilisateur.
