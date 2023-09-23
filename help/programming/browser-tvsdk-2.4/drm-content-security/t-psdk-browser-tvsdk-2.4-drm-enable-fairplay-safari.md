---
description: Vous pouvez activer FairPlay pour Safari lorsque vous utilisez Primetime DRM Cloud, optimisé par ExpressPlay.
title: Activation de FairPlay pour Safari HLS
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Activation de FairPlay pour Safari HLS {#enable-fairplay-for-safari-hls}

Vous pouvez activer FairPlay pour Safari lorsque vous utilisez Primetime DRM Cloud, optimisé par ExpressPlay.

Vérifiez que vous disposez des éléments suivants :

* Exemple d’application fonctionnel pouvant lire la vidéo HLS.

  L’exemple d’application doit pouvoir lire du contenu protégé par FairPlay avec les licences gérées via Primetime DRM optimisées par ExpressPlay.
* Exemple de contenu HLS (un manifeste M3U8) fourni avec la protection FairPlay.

Pour tirer pleinement parti des informations présentées ici, découvrez les processus multi-DRM commençant par la sous-section . [Serveur de référence : exemple de serveur de droits ExpressPlay (SEES)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_multi_drm_workflows.pdf) dans le guide Workflows multi-DRM . Lisez d’abord cette documentation sur la configuration de vos droits et de votre serveur clé. Les informations ci-dessous seront beaucoup plus utiles.
Vous avez besoin des éléments suivants :

* Votre *production* Authentificateur client à partir d’ExpressPlay
* la même clé de contenu et `iv` avec lequel votre contenu a été mis en package.
* L’emplacement de votre certificat de clé publique FairPlay.

Pour modifier votre application FairPlay/Safari :

1. Définissez l’emplacement de votre certificat de clé publique FairPlay utilisé dans la demande de serveur de licences FairPlay.

   Par exemple :

   ```js
   var myServerCertificatePath = './my_fairplay.cer';
   ```

1. Effectuer une licence FairPlay manuelle *token* demande à ExpressPlay d’obtenir une URL de jeton de licence.

       Vous pouvez effectuer cette étape de l’une des manières suivantes :
   
   * Utilisez votre propre authentificateur client de production ExpressPlay.
   * Utilisez la même clé de contenu et `iv` dans cette requête qui a été utilisée pour regrouper le contenu que vous souhaitez lire.

     Exécutez la commande suivante à partir du shell et remplacez votre authentificateur client ExpressPlay pour obtenir l’URL du jeton de licence de l’exemple de contenu :

     ```
     curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
          customerAuthenticator=<ExpressPlay customer authenticator identifier>& 
          errorFormat=json& 
          contentKey=<your content key>& 
          iv=<your iv here>"
     ```

     La réponse avec l’URL du jeton de licence se présente comme suit :

     ```
     https://fp.service.expressplay.com:80/hms/fp/rights/? 
          ExpressPlayToken=<base64-encoded ExpressPlay token>
     ```

1. Définissez une variable avec l’URL du jeton de licence d’ExpressPlay.

   Par exemple :

   ```js
   var myServerProcessSPCPath = 'https://fp.service.expressplay.com:80/hms/fp/rights/? 
        ExpressPlayToken=<base64-encoded ExpressPlay token>';
   ```

1. Avant que votre application puisse lire du contenu protégé, modifiez le modèle d’URL du contenu depuis `skd://` to `https://`.

   Vous devez ajouter ce changement de schéma d’URL dans votre application, avant l’appel au serveur de licences qui permet la lecture.

   Les protocoles doivent être modifiés, car l’ID de contenu, qui permet d’accéder à la clé de contenu dans le système de gestion des clés, est inclus dans le manifeste M3U8 avec la variable `skd://` protocole . Lorsque le lecteur est prêt à obtenir la licence pour lire le contenu protégé, il doit d’abord changer de protocole pour communiquer avec le serveur de licences ExpressPlay. Dans l’exemple ci-dessous, la variable `myServerProcessSPCPath` est modifié pour contenir le modèle d’URL correct pour la demande de serveur de licences :

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
