---
description: La prise en charge de l’attribut withCredentials dans XMLHttpRequests permet aux requêtes de partage de ressources cross-origin (CORS) d’inclure les cookies du domaine cible pour divers types de requêtes.
keywords: CORS;cross-origin;partage des ressources;cookies;withCredentials
title: Partage de ressources cross-origin
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Partage de ressources cross-origin {#cross-origin-resource-sharing}

La prise en charge de l’attribut withCredentials dans XMLHttpRequests permet aux requêtes de partage de ressources cross-origin (CORS) d’inclure les cookies du domaine cible pour divers types de requêtes.

Lorsque le client demande un manifeste, un segment ou une clé, le serveur peut définir un cookie que le client doit transmettre pour les requêtes suivantes. Pour permettre la lecture et l’écriture de cookies, le client doit définir la variable `withCredentials` Attribuer à `true` pour les demandes d’origine croisée.

Pour activer `withCredentials` prise en charge de la plupart des types de requêtes lors de la lecture d’une ressource multimédia donnée :

1. Créez le `CORSConfig` .

   ```js
   var corsConfig = new AdobePSDK.CORSConfig();  
   corsConfig.enableEncryptionRequest = true; 
   ```

1. Joindre la variable `corsConfig` à la fonction `NetworkConfiguration` objet et définition `useCookieHeaderForAllRequests` to `true`.

   ```js
   var networkConfig = new AdobePSDK.NetworkConfiguration();  
   networkConfig.CORSConfig = corsConfig; 
   networkConfiguration.useCookieHeaderForAllRequests= true;
   ```

1. Définir `networkConfig` dans le `MediaPlayerItemConfig` .

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig();  
   mediaPlayerItemConfig.networkConfiguration = networkConfig; 
   ```

1. Pass `MediaPlayerItemConfig` à la fonction `MediaPlayer.replaceCurrentResource` .

   ```js
   var player = new AdobePSDK.MediaPlayer(); 
   mediaResource = new AdobePSDK.MediaResource(url, AdobePSDK.MediaResourceType.HLS);  
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);  
   ```

>[!IMPORTANT]
>
>La variable `useCookieHeaderForAllRequests` L’indicateur n’affecte pas les demandes de licence. Pour définir la variable `withCredentials` Attribuer à `true` pour une demande de licence, vous devez définir la variable `withCredentials` dans vos données de protection ou spécifiez une clé d’autorisation dans la variable `httpRequestHeaders` de vos données de protection. Par exemple :

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

L’indicateur n’affecte pas une demande de licence, car certains serveurs définissent la variable `Access-Control-Allow-Origin` champ au caractère générique (&#39;&#42;&quot;) dans leur réponse. Mais, lorsque l’indicateur d’identification est défini sur `true`, le caractère générique ne peut pas être utilisé dans `Access-Control-Allow-Origin`. Si vous définissez `useCookieHeaderForAllRequests` to `true` pour tous les types de demandes, l’erreur suivante peut s’afficher pour une demande de licence :

Gardez à l’esprit les informations suivantes :

* Lors d’un appel avec `withCredentials=true` échec, le navigateur TVSDK tente à nouveau l’appel sans `withCredentials`.
* Lorsqu’un appel est effectué avec `networkConfiguration.useCookieHeaderForAllRequests=false`, les requêtes XHR sont effectuées sans le `withCredentials` attribut.
