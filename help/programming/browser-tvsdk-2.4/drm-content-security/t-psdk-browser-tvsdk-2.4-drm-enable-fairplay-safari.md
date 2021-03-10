---
description: Vous pouvez activer FairPlay pour Safari lorsque vous travaillez avec Primetime DRM Cloud, optimisé par ExpressPlay.
title: Activer FairPlay pour Safari HLS
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---


# Activer FairPlay pour Safari HLS {#enable-fairplay-for-safari-hls}

Vous pouvez activer FairPlay pour Safari lorsque vous travaillez avec Primetime DRM Cloud, optimisé par ExpressPlay.

Vérifiez que vous disposez des éléments suivants :

* Exemple d’application fonctionnel qui peut lire la vidéo HLS.

   L’exemple d’application doit être capable de lire du contenu protégé par FairPlay avec les licences gérées via Primetime DRM optimisées par ExpressPlay.
* Exemple de contenu HLS (un manifeste M3U8) fourni avec la protection FairPlay.

Pour utiliser pleinement les informations ici, découvrez les Workflows multiDRM en commençant par la sous-section [Serveur de référence : Exemple de serveur de droits ExpressPlay (SEES)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_multi_drm_workflows.pdf) dans le guide des Workflows multiDRM. Lisez d&#39;abord cette documentation sur la configuration de vos droits et de votre serveur clé, et les informations ci-dessous seront beaucoup plus utiles.
Vous avez besoin des éléments suivants :

* Votre *production* Authentificateur client d&#39;ExpressPlay
* La même clé de contenu et `iv` avec laquelle votre contenu a été compressé.
* Emplacement de votre certificat de clé publique FairPlay.

Pour modifier votre application FairPlay / Safari :

1. Définissez l’emplacement de votre certificat de clé publique FairPlay qui a été utilisé dans la demande de serveur de licences FairPlay.

   Par exemple :

   ```js
   var myServerCertificatePath = './my_fairplay.cer';
   ```

1. Effectuez une demande manuelle de licence FairPlay *token* à ExpressPlay pour obtenir une URL de jeton de licence.

       Vous pouvez exécuter cette étape de l’une des manières suivantes :
   
   * Utilisez votre propre authentificateur de client de production ExpressPlay.
   * Utilisez la même clé de contenu et `iv` dans cette requête qui a été utilisée pour regrouper le contenu à lire.

      Exécutez la commande suivante à partir du shell et substituez votre authentificateur de client ExpressPlay pour obtenir l’URL du jeton de licence pour l’exemple de contenu :

      ```
      curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
           customerAuthenticator=<ExpressPlay customer authenticator identifier>& 
           errorFormat=json& 
           contentKey=<your content key>& 
           iv=<your iv here>"
      ```

      La réponse avec l’URL du jeton de licence ressemblera à ceci :

      ```
      https://fp.service.expressplay.com:80/hms/fp/rights/? 
           ExpressPlayToken=<base64-encoded ExpressPlay token>
      ```

1. Définissez une variable avec l’URL du jeton de licence d’ExpressPlay.

   Par exemple :

   ```js
   var myServerProcessSPCPath = 'https://fp.service.expressplay.com:80/hms/fp/rights/? 
        ExpressPlayToken=<base64-encoded ExpressPlay token>';
   ```

1. Avant que votre application puisse lire le contenu protégé, remplacez le modèle d’URL du contenu `skd://` par `https://`.

   Vous devez ajouter ce changement de schéma d’URL dans votre application, avant l’appel au serveur de licences qui permet la lecture.

   Les protocoles doivent être modifiés car l&#39;ID de contenu, qui permet d&#39;accéder à la clé de contenu dans le système de gestion des clés, est inclus dans le manifeste M3U8 avec le protocole `skd://`. Lorsque le lecteur est prêt à obtenir la licence pour lire le contenu protégé, il doit d&#39;abord changer de protocole pour communiquer avec le serveur de licences ExpressPlay. Dans l’exemple ci-dessous, `myServerProcessSPCPath` est modifié pour contenir le modèle d’URL correct pour la demande de serveur de licences :

   ```js
   extractContentId(initData) {  
       contentId = arrayToString(initData); // contentId is passed up as a URI,  
                                            // from which the host must be extracted:  
       var link = document.createElement('a');  
       link.href = contentId;  
       var index = contentId.indexOf(':');  
       myServerProcessSPCPath = "https:" + contentId.substring(index+1);  
       console.log("severProcessSPCPAth = " + serverProcessSPCPath); return link.hostname;  
   }
   ```

