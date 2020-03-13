---
description: La prise en charge de l’attribut withCredentials dans XMLHttpRequests permet aux demandes de partage de  de ressources entre  (CORS) d’inclure les cookies du domaine pour divers types de requêtes.
keywords: CORS;cross origin;resource sharing;cookies;withCredentials
seo-description: La prise en charge de l’attribut withCredentials dans XMLHttpRequests permet aux demandes de partage de  de ressources entre  (CORS) d’inclure les cookies du domaine pour divers types de requêtes.
seo-title: 'Partage de  de ressources entre '
title: 'Partage de  de ressources entre '
uuid: e788b542-d4ac-48aa-91e2-1e88068cbba1
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Partage de  de ressources entre {#cross-origin-resource-sharing}

La prise en charge de l’attribut withCredentials dans XMLHttpRequests permet aux demandes de partage de  de ressources entre  (CORS) d’inclure les cookies du domaine pour divers types de requêtes.

Lorsque le client demande un manifeste, un segment ou une clé, le serveur peut définir un cookie que le client doit transmettre pour les requêtes suivantes. Pour permettre la lecture et l’écriture de cookies, le client doit définir l’ `withCredentials` attribut sur `true` pour les requêtes  croisées .

Pour activer la `withCredentials` prise en charge de la plupart des types de requêtes lors de la lecture d’une ressource multimédia donnée :

1. Créez l’ `CORSConfig` objet.

   ```js
   var corsConfig = new AdobePSDK.CORSConfig();  
   corsConfig.enableEncryptionRequest = true; 
   ```

1. Joignez l’objet `corsConfig` à l’ `NetworkConfiguration` objet et définissez `useCookieHeaderForAllRequests` sur `true`.

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
>L’ `useCookieHeaderForAllRequests` indicateur n’affecte pas les demandes de licence. Pour définir l’ `withCredentials` attribut `true` pour une demande de licence, vous devez définir l’ `withCredentials` attribut dans vos données de protection ou spécifier une clé d’autorisation dans `httpRequestHeaders` les données de protection. Par exemple :

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

L&#39;indicateur n&#39;affecte pas une demande de licence, car certains serveurs définissent le `Access-Control-Allow-Origin` champ sur un caractère générique (&#39;*&#39;) dans leur réponse. Mais lorsque l’indicateur d’identification est défini sur `true`, le caractère générique ne peut pas être utilisé dans `Access-Control-Allow-Origin`. Si vous définissez `useCookieHeaderForAllRequests` sur `true` pour tous les types de requêtes, l’erreur suivante peut s’afficher pour une demande de licence :

Tenez compte des informations suivantes :

* Lorsqu’un appel avec `withCredentials=true` échoue, le navigateur TVSDK  l’appel sans `withCredentials`.
* Lorsqu’un appel est effectué avec `networkConfiguration.useCookieHeaderForAllRequests=false`, les requêtes XHR sont effectuées sans l’ `withCredentials` attribut.