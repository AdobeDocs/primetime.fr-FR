---
description: La prise en charge de l’attribut withCredentials dans XMLHttpRequests permet aux demandes CORS (partage de ressources entre origines) d’inclure les cookies du domaine de cible pour divers types de requêtes.
keywords: CORS ; origine croisée ; partage de ressources ; cookies ; avecCredentials
title: Partage de ressources entre origines
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---


# Partage de ressources entre origines {#cross-origin-resource-sharing}

La prise en charge de l’attribut withCredentials dans XMLHttpRequests permet aux demandes CORS (partage de ressources entre origines) d’inclure les cookies du domaine de cible pour divers types de requêtes.

Lorsque le client demande un manifeste, un segment ou une clé, le serveur peut définir un cookie que le client doit transmettre pour les demandes suivantes. Pour permettre la lecture et l’écriture de cookies, le client doit définir l’attribut `withCredentials` sur `true` pour les demandes inter-origines.

Pour activer la prise en charge de `withCredentials` pour la plupart des types de requêtes lors de la lecture d&#39;une ressource de média donnée :

1. Créez l’objet `CORSConfig`.

   ```js
   var corsConfig = new AdobePSDK.CORSConfig();  
   corsConfig.enableEncryptionRequest = true; 
   ```

1. Joignez `corsConfig` à l&#39;objet `NetworkConfiguration` et définissez `useCookieHeaderForAllRequests` sur `true`.

   ```js
   var networkConfig = new AdobePSDK.NetworkConfiguration();  
   networkConfig.CORSConfig = corsConfig; 
   networkConfiguration.useCookieHeaderForAllRequests= true;
   ```

1. Définissez `networkConfig` dans l&#39;objet `MediaPlayerItemConfig`.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig();  
   mediaPlayerItemConfig.networkConfiguration = networkConfig; 
   ```

1. Transmettez `MediaPlayerItemConfig` à la méthode `MediaPlayer.replaceCurrentResource`.

   ```js
   var player = new AdobePSDK.MediaPlayer(); 
   mediaResource = new AdobePSDK.MediaResource(url, AdobePSDK.MediaResourceType.HLS);  
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);  
   ```

>[!IMPORTANT]
>
>L&#39;indicateur `useCookieHeaderForAllRequests` n&#39;affecte pas les demandes de licence. Pour définir l&#39;attribut `withCredentials` sur `true` pour une demande de licence, vous devez définir l&#39;attribut `withCredentials` dans vos données de protection ou spécifier une clé d&#39;autorisation dans `httpRequestHeaders` de vos données de protection. Par exemple :

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

L&#39;indicateur n&#39;affecte pas une demande de licence, car certains serveurs définissent le champ `Access-Control-Allow-Origin` sur un caractère générique (&#39;*&#39;) dans leur réponse. Cependant, lorsque l&#39;indicateur d&#39;identification est défini sur `true`, le caractère générique ne peut pas être utilisé dans `Access-Control-Allow-Origin`. Si vous définissez `useCookieHeaderForAllRequests` sur `true` pour tous les types de requêtes, l’erreur suivante peut s’afficher pour une demande de licence :

Rappelez-vous des informations suivantes :

* Si un appel avec `withCredentials=true` échoue, le navigateur TVSDK Reprises l’appel sans `withCredentials`.
* Lorsqu’un appel est effectué avec `networkConfiguration.useCookieHeaderForAllRequests=false`, les requêtes XHR sont effectuées sans l’attribut `withCredentials`.