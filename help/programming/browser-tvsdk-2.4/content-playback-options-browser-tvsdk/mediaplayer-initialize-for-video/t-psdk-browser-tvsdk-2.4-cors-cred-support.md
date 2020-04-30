---
description: La prise en charge de l’attribut withCredentials dans XMLHttpRequests permet aux demandes CORS (partage de ressources entre origines) d’inclure les cookies du domaine de cible pour divers types de requêtes.
keywords: CORS;cross origin;resource sharing;cookies;withCredentials
seo-description: La prise en charge de l’attribut withCredentials dans XMLHttpRequests permet aux demandes CORS (partage de ressources entre origines) d’inclure les cookies du domaine de cible pour divers types de requêtes.
seo-title: Partage de ressources entre origines
title: Partage de ressources entre origines
uuid: e788b542-d4ac-48aa-91e2-1e88068cbba1
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Partage de ressources entre origines {#cross-origin-resource-sharing}

La prise en charge de l’attribut withCredentials dans XMLHttpRequests permet aux demandes CORS (partage de ressources entre origines) d’inclure les cookies du domaine de cible pour divers types de requêtes.

Lorsque le client demande un manifeste, un segment ou une clé, le serveur peut définir un cookie que le client doit transmettre pour les demandes suivantes. Pour permettre la lecture et l’écriture de cookies, le client doit définir l’ `withCredentials` attribut sur `true` pour les requêtes inter-origines.

Pour activer la `withCredentials` prise en charge de la plupart des types de requêtes lors de la lecture d’une ressource multimédia donnée :

1. Créez l’ `CORSConfig` objet.

   ```js
   var corsConfig = new AdobePSDK.CORSConfig();  
   corsConfig.enableEncryptionRequest = true; 
   ```

1. Joignez l’objet `corsConfig` à l’ `NetworkConfiguration` objet et définissez `useCookieHeaderForAllRequests` la valeur `true`.

   ```js
   var networkConfig = new AdobePSDK.NetworkConfiguration();  
   networkConfig.CORSConfig = corsConfig; 
   networkConfiguration.useCookieHeaderForAllRequests= true;
   ```

1. Défini `networkConfig` dans l’ `MediaPlayerItemConfig` objet.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig();  
   mediaPlayerItemConfig.networkConfiguration = networkConfig; 
   ```

1. Passez `MediaPlayerItemConfig` à la `MediaPlayer.replaceCurrentResource` méthode.

   ```js
   var player = new AdobePSDK.MediaPlayer(); 
   mediaResource = new AdobePSDK.MediaResource(url, AdobePSDK.MediaResourceType.HLS);  
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);  
   ```

>[!IMPORTANT]
>
>L&#39; `useCookieHeaderForAllRequests` indicateur n&#39;affecte pas les demandes de licence. Pour définir l&#39; `withCredentials` attribut sur `true` pour une demande de licence, vous devez définir l&#39;attribut `withCredentials` dans vos données de protection ou spécifier une clé d&#39;autorisation dans les `httpRequestHeaders` données de protection. Par exemple :

```
# Example 1 
{ 
    "com.widevine.alpha": {  
        "withCredentials":true,  
        "serverURL":  
          "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=[YOUR_TOKEN</i]" } 
} 
 
# Example 2 
{ 
    "com.widevine.alpha": { 
        "httpRequestHeaders": {  
            "authorization": "true"  
            }, 
        "serverURL":  
          "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=[YOUR_TOKEN</i>]" }
        } 
}
```

L&#39;indicateur n&#39;affecte pas une demande de licence, car certains serveurs définissent le `Access-Control-Allow-Origin` champ sur un caractère générique (&#39;*&#39;) dans leur réponse. Cependant, lorsque l’indicateur d’identification est défini sur `true`, le caractère générique ne peut pas être utilisé dans `Access-Control-Allow-Origin`. Si vous définissez `useCookieHeaderForAllRequests` sur `true` pour tous les types de requêtes, l’erreur suivante peut s’afficher pour une demande de licence :

Rappelez-vous des informations suivantes :

* En cas d’échec d’un appel `withCredentials=true` , le navigateur TVSDK Reprises l’appel sans `withCredentials`.
* Lorsqu’un appel est effectué avec `networkConfiguration.useCookieHeaderForAllRequests=false`, les requêtes XHR sont effectuées sans l’ `withCredentials` attribut.