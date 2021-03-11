---
description: Vous pouvez utiliser le gestionnaire de package Bento4 d'ExpressPlay pour préparer le contenu pour toutes les solutions DRM prises en charge par Primetime Cloud DRM, optimisé par ExpressPlay.
title: ExpressPlay Packager / Cloud DRM / TVSDK
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---


# ExpressPlay Packager / Cloud DRM / TVSDK {#expressplay-packager-cloud-drm-tvsdk}

Vous pouvez utiliser le gestionnaire de package Bento4 d&#39;ExpressPlay pour préparer le contenu pour toutes les solutions DRM prises en charge par Primetime Cloud DRM, optimisé par ExpressPlay.

Cette tâche décrit comment utiliser un outil tiers pour préparer du contenu protégé, dans ce cas *Outils ExpressPlay Bento4*, pour une utilisation avec diverses solutions DRM. Pour plus d&#39;informations, consultez la documentation *Outils Bento4* sur le [site Web ExpressPlay](https://www.expressplay.com/developer/).
1. Achetez un compte ExpressPlay et obtenez vos informations d’authentification du client ExpressPlay.

   Voir [début rapide de DRM Cloud Primetime.](../../quick-start/quick-overview.md)
1. Si vous chiffrez du contenu pour Primetime Access, procurez-vous le SDK Primetime Adobe Access à partir de l’Adobe, ainsi que les certificats requis (certificat de licence, certificat de transport et certificat d’emballage).
1. Fournissez une clé de chiffrement de contenu (CEK) et un Enregistrement de clé de chiffrement de contenu (CEKSID) pour l’utiliser sur les systèmes DRM. (Vous les générez de manière aléatoire à l’aide d’OpenSSL ou d’autres méthodes similaires.)

   Le CEK est la clé réelle que vous utilisez pour chiffrer vos fichiers vidéo. Vous pouvez soit le stocker en toute sécurité sur votre propre serveur dans votre propre système de gestion des clés, soit utiliser la [solution d&#39;enregistrement de clés](https://www.expressplay.com/developer/key-storage/) d&#39;ExpressPlay.

   Un CEKSID est l’identifiant d’un CEK particulier. Vous ne transmettez pas (généralement) la clé de chiffrement. Par exemple, lorsque vous demandez un jeton de licence, vous fournissez le CEKSID.

1. Si vous chiffrez du contenu pour Access, utilisez votre CEK pour créer des métadonnées d’accès Primetime associées à votre contenu.

1. Fragmentez votre contenu pour le préparer à l&#39;outil *Bento4 MP4DASH*.

   Pour cette étape, vous pouvez utiliser l’outil *MP4FRAGMENT*. Vous n’avez besoin de fragmenter votre contenu qu’une seule fois. Par exemple :

   ```
   ./mp4fragment Unfragmented.mp4 Fragmented.mp4
   ```

1. Utilisez l&#39;outil *Bento4 MPDASH* pour &quot;ify-DASH&quot; et chiffrer votre contenu fragmenté.

   Utilisez cette commande pour spécifier tous les systèmes DRM que vous utiliserez et transmettre toutes les métadonnées d&#39;accès Primetime générées à partir des étapes précédentes. Par exemple :

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
   
   1. Sélection du contenu par le client. Cette implémentation doit inclure un point de terminaison permettant aux clients de demander un jeton de contenu pour un ID de contenu spécifique.
   1. Droits du client
   1. Demandes de jeton de licence (ExpressPlay) du client ( [Demande de jeton de licence ExpressPlay / référence de réponse](../../license-token-req-resp-ref/license-req-resp-overview.md))

1. Créez votre client.

   Le client doit inclure un appel à votre serveur de stockage. L’Adobe recommande au client d’appeler la vitrine une fois que l’utilisateur a sélectionné du contenu et une fois l’utilisateur authentifié. Ensuite, transmettez le jeton renvoyé d’ExpressPlay à votre lecteur pour l’utiliser pour les demandes de licence. Vous trouverez ci-dessous des informations sur la mise en oeuvre du composant DRM de vos lecteurs :

   * Kit de développement TVSDK du navigateur pour HTML5
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. Avec le jeton de licence en main, le client peut maintenant dériver l’URL de demande du jeton et demander la licence à ExpressPlay, puis lire le contenu sélectionné et protégé pour l’utilisateur.
