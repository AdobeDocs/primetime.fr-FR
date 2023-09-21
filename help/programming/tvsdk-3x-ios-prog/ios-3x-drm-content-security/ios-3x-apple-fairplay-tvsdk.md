---
description: Pour mettre en oeuvre FairPlay Streaming dans votre application TVSDK, vous devez écrire un Resource Loader, qui envoie une demande d’acquisition de licence à votre serveur FairPlay Streaming.
title: Apple FairPlay dans les applications TVSDK
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# Apple FairPlay dans les applications TVSDK {#apple-fairplay-in-tvsdk-applications}

Pour mettre en oeuvre FairPlay Streaming dans votre application TVSDK, vous devez écrire un Resource Loader, qui envoie une demande d’acquisition de licence à votre serveur FairPlay Streaming.

Le code Resource Loader est responsable des tâches suivantes :

1. Déterminez où envoyer la demande d’acquisition de licence.
1. Mettez la requête en forme.
1. Fournissez les informations nécessaires au serveur, de sorte que le serveur puisse décider si la demande doit être autorisée.

Par exemple, si vous utilisez le DRM Primetime Cloud d’Adobe optimisé par ExpressPlay, votre chargeur de ressources envoie la demande à :

```
https://fp-gen.service.expressplay.com
```

Le chargeur de ressources formate la requête et joint un jeton ExpressPlay qui autorise la lecture à l’URL. Lors de l’acquisition du jeton ExpressPlay, plusieurs options sont à prendre en compte. Ces options sont déterminées par la manière dont vous avez empaqueté votre contenu.

Lorsque vous compressez votre contenu, le module insère `skd:` URL dans votre manifeste M3U8. Après la `skd:` , vous pouvez placer n’importe quelle donnée dans le manifeste . Vous pouvez utiliser ces données dans le code de votre application pour effectuer les tâches répertoriées ci-dessus. Par exemple, vous pouvez utiliser `skd:{content_id}` afin que votre application puisse déterminer l’identifiant du contenu en cours de lecture et demander un jeton pour cette partie spécifique de contenu. Vous pouvez également, par exemple, utiliser `skd:{entitlement_server_url}?cid={content_id}`, de sorte que votre application n’ait pas besoin d’avoir l’URL du serveur de droits codée en dur.

Il se peut que vous n’ayez pas besoin d’informations dans votre `skd:` URL si, au démarrage de la lecture, vous connaissez déjà l’ID de contenu par le biais d’autres canaux. Le deuxième exemple est une solution idéale pour tester votre configuration, mais vous pouvez également l’utiliser dans un environnement de production.

>[!TIP]
>
>Vous déterminez le format de `skd:`.

Votre contenu est obtenu en utilisant la variable `skd:` , mais votre demande de licence utilise `https:`. Les options les plus courantes pour traiter ces protocoles sont les suivantes :

* **Test initial de la lecture de bout en bout** Lors de la création du module, sélectionnez une `skd:` URL. Lors du test de votre application, acquérez manuellement une licence à partir d’ExpressPlay et codez-la en dur (une `https:` URL) et URL du contenu dans votre chargeur.

  Par exemple :

  ```
  NSString* const PLAYLIST_URL =  
    @"https://{your_content_URL}/{your_manifest}.m3u8"; 
  NSString* const EXPRESSPLAY_TOKEN =  
    @"https://fp.service.expressplay.com:80/hms/fp/rights/? 
      ExpressPlayToken={copy_your_token_to_here}";
  ```

* **La plupart des autres cas** Lors de la création du module, sélectionnez une `skd:` URL représentant de manière unique l’identifiant du contenu. Dans votre chargeur, analysez la variable `skd:` URL, envoyez-la à votre serveur pour acquérir un jeton et utilisez le jeton obtenu comme URL.

  Par exemple :

  ```
  - (BOOL)resourceLoader:(AVAssetResourceLoader *)resourceLoader  
        shouldWaitForLoadingOfRequestedResource:(AVAssetResourceLoadingRequest *)loadingRequest { 
      NSURL *url = [[loadingRequest request] URL]; 
      if (![[url scheme] isEqual:@"skd"]) 
          return NO; 
  
      NSString *strUrl = [url absoluteString]; 
      NSLog(@"url is: %@", strUrl); 
  
      strUrl = [strUrl stringByReplacingOccurrencesOfString:@"skd://" withString:@"https://"]; 
  
      NSData *assetId; 
  
      NSData *requestBytes; 
      NSError* error = nil; 
      BOOL handled = NO; 
  
      NSData  *responseData = nil; 
  
      assetId = getMyAssetIdentifierFromURL(url); 
  
      /* Usecase 1: "On Premise Fairplay Server" 
       * Set the strUrl to the OnPremise Fairplay Server Url. The OnPremise Fairplay  
       * Server Url is either hardcoded in the App or derived from strUrl. 
       */ 
  #if 0  
      // Insert your use case 1 codes here: 
      // strUrl = getOnPremiseServerUrl(strUrl, assetId); 
  #endif // 
  
      /* Usecase 2: The strUrl is the entitlement server. 
       * Send assetId to the entitlement server; if the user is allowed to playback  
       * the content, the entitlement server will send back an ExpressPlay Token Url. 
       */ 
  
  #if 0 
      // The hardcoded SEES server: 
      strUrl = @"https://10.0.248.85:8080/sees/SEESServlet"; 
  
      // You can use the following code to simulate a device binding entitlement  
      // request:  
      // First, invoke getExpressPlayTokenUrlFromEntilementServer with  
      // bEnforceDeviceID set to false. When you play the content, the device_id  
      // will be registered on the ExpressPlay Server.  Now change code to set  
      // bEnforceDeviceID to true, and rerun the program. The ExpressPlay token  
      // sent back by the SEES server will be device bound. 
  
      // The strUrl returned below is the ExpressPlay Token URL. 
      strUrl = getExpressPlayTokenUrlFromEntilementServer(strUrl, assetId, true, &error); 
  #endif 
  
      /* Usecase 3: The strUrl is already the ExpressPlay Token Url. 
       */ 
  
      // Read in the certificate 
      NSLog(@"Get Application Certificate"); 
      NSString* certPath = [[NSBundle mainBundle] pathForResource:@"my_certificate.cer"  
                                                           ofType:nil]; 
  
      NSData *appCert = [NSData dataWithContentsOfFile:certPath]; 
  
      // To create the request blob for the server: 
      requestBytes = [loadingRequest streamingContentKeyRequestDataForApp: appCert 
                                                        contentIdentifier:assetId  
                                                                  options:nil  
                                                                    error:&error]; 
      if (requestBytes == nil) { 
          NSLog(@"Error creating server request: %@", error); 
          return false; 
      } 
      // Per the specification, send requestBytes along with the assetId to the Key 
      // Server and obtain the response. 
      NSError *err; 
  
      responseData = getCKCFromExpressPlayService( strUrl, requestBytes, assetId, &err); 
  
      if (responseData != nil) { 
          NSLog(@"Get response data: "); 
          [loadingRequest finishLoadingWithResponse:nil  
                                               data:(NSData *)responseData 
                                           redirect:nil]; 
      } 
      else { 
          [loadingRequest finishLoadingWithError:err]; 
          NSLog(@"bad key response"); 
      } 
      handled = YES; 
  bail: 
      return handled; 
  
  }
  ```

## Activer Apple FairPlay dans les applications TVSDK {#section_61CFA3C22FE64F52B2C8CE860B72E88B}

Vous pouvez mettre en oeuvre Apple FairPlay Streaming, qui est une solution DRM Apple, dans vos applications TVSDK.

1. Créez votre chargeur de ressources client FairPlay en implémentant `PTAVAssetResourceLoaderDelegate`. Pour plus d’informations, voir Apple FairPlay dans les applications TVSDK.

   >[!NOTE]
   >
   >Veillez à suivre les instructions de la section *Guide du programme de diffusion en continu FairPlay* ( *FairPlayStreaming_PG.pdf*), qui est inclus dans [SDK du serveur FairPlay pour le développement d’une application tenant compte de FPS](https://developer.apple.com/services-account/download?path=/Developer_Tools/FairPlay_Streaming_SDK/FairPlay_Streaming_Server_SDK.zip)).

   La méthode `resourceLoader:shouldWaitForLoadingOfRequestedResource` équivaut à ce qui se trouve dans `AVAssetResourceLoaderDelegate`.

   >[!NOTE]
   >
   >Dans le scénario du serveur de licences ExpressPlay , pour lire le contenu, modifiez le modèle d’URL dans l’URL de demande de licence de serveur ExpressPlay à partir de `skd://` to `https://` (ou `https://`).

1. Enregistrez le *FairPlay* Customer Resource Loader avec `registerPTAVAssetResourceLoader`.

   ```
   PTFairPlayResourceLoader *resourceLoader =  
     [[PTFairPlayResourceLoader new] autorelease];  
   [[PTDefaultMediaPlayerClientFactory defaultFactory]  
     registerPTAVAssetResourceLoader:resourceLoader];
   ```

   >[!NOTE]
   >
   >Si vous avez écrit votre propre serveur de licences FairPlay ou si vous utilisez un serveur de licences FairPlay tiers, consultez le fournisseur de votre serveur de licences pour déterminer l’URL, le formatage et toute autre exigence de votre serveur de licences.
