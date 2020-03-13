---
description: Pour mettre en oeuvre FairPlay Streaming dans votre application TVSDK, vous devez écrire un chargeur de ressources, qui envoie une demande d’acquisition de licence à votre serveur FairPlay Streaming.
seo-description: Pour mettre en oeuvre FairPlay Streaming dans votre application TVSDK, vous devez écrire un chargeur de ressources, qui envoie une demande d’acquisition de licence à votre serveur FairPlay Streaming.
seo-title: Apple FairPlay dans les applications TVSDK
title: Apple FairPlay dans les applications TVSDK
uuid: 4384d379-37cd-46c5-8c25-0cda16bdebb8
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Apple FairPlay dans les applications TVSDK {#apple-fairplay-in-tvsdk-applications}

Pour mettre en oeuvre FairPlay Streaming dans votre application TVSDK, vous devez écrire un chargeur de ressources, qui envoie une demande d’acquisition de licence à votre serveur FairPlay Streaming.

Le code du chargeur de ressources est responsable du  de suivant :

1. Déterminez où envoyer la demande d’acquisition de licence.
1. Mettez en forme la requête.
1. Fournissez les informations nécessaires au serveur afin que le serveur puisse décider si la requête doit être autorisée.

Par exemple, si vous utilisez la gestion des droits numériques d’Adobe Primetime Cloud optimisée par ExpressPlay, votre chargeur de ressources envoie la demande à :

```
https://fp-gen.service.expressplay.com
```

Le chargeur de ressources formate la requête et associe un jeton ExpressPlay qui autorise la lecture à l’URL. Lors de l’acquisition du jeton ExpressPlay, plusieurs options sont à prendre en compte. Ces options sont déterminées par la manière dont vous avez compressé votre contenu.

Lorsque vous assemblez votre contenu, le gestionnaire de package insère `skd:` des URL dans votre manifeste M3U8. Après l’ `skd:` entrée, vous pouvez placer n’importe quelle donnée dans le manifeste. Vous pouvez utiliser ces données dans le code de votre application pour terminer les  de répertoriées ci-dessus. Vous pouvez, par exemple, utiliser `skd:{content_id}` cette fonction pour que votre application puisse déterminer l’ID du contenu en cours de lecture et demander un jeton pour ce contenu spécifique. Vous pouvez également, par exemple, utiliser `skd:{entitlement_server_url}?cid={content_id}`, de sorte que votre application n’ait pas besoin d’avoir l’URL du serveur de droits codée en dur.

Il se peut que vous n’ayez pas besoin d’informations dans votre `skd:` URL si, lors de la  de lecture, vous connaissez déjà l’ID de contenu par le biais d’autres . Le deuxième exemple est une solution idéale pour tester votre configuration, mais vous pouvez également l’utiliser dans un  de  de production.

>[!TIP]
>
>Vous déterminez le format de `skd:`.

Votre contenu est obtenu à l’aide du `skd:` protocole, mais votre demande de licence utilise `https:`. Les options les plus courantes pour traiter ces protocoles sont les suivantes :

* **Tests initiaux de lecture** de bout en bout Lors de l’assemblage de votre contenu, sélectionnez une `skd:` URL. Lors du test de votre application, acquérez manuellement une licence auprès d’ExpressPlay et codez en dur la licence (une `https:` URL) et l’URL de contenu dans votre chargeur.

   Par exemple :

   ```
   NSString* const PLAYLIST_URL =  
     @"https://{your_content_URL}/{your_manifest}.m3u8"; 
   NSString* const EXPRESSPLAY_TOKEN =  
     @"https://fp.service.expressplay.com:80/hms/fp/rights/? 
       ExpressPlayToken={copy_your_token_to_here}";
   ```

* **Dans la plupart des autres cas** , lors de l’assemblage de votre contenu, sélectionnez une `skd:` URL qui représente de manière unique l’ID du contenu. Dans votre chargeur, analysez l’ `skd:` URL, envoyez-la à votre serveur pour acquérir un jeton et utilisez le jeton résultant comme URL.

   Par exemple :

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

## Activation d’Apple FairPlay dans les applications TVSDK{#enable-apple-fairplay-in-tvsdk-applications}

Vous pouvez mettre en oeuvre la diffusion en flux continu FairPlay d’Apple, qui est la solution DRM d’Apple, dans vos applications TVSDK.

1. Créez votre chargeur de ressources client FairPlay en implémentant `PTAVAssetResourceLoaderDelegate`.

   Pour plus d’informations, voir [Apple FairPlay dans les applications](../../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md)TVSDK.

   >[!NOTE]
   >
   >Assurez-vous de suivre les instructions du Guide *FairPlay Streaming* ( *FairPlayStreaming_PG.pdf*), inclus dans le SDK [FairPlay Server pour le développement d’une application](https://developer.apple.com/services-account/download?path=/Developer_Tools/FairPlay_Streaming_SDK/FairPlay_Streaming_Server_SDK.zip)compatible FPS).

   La `resourceLoader:shouldWaitForLoadingOfRequestedResource` méthode est équivalente à ce qui se trouve dans `AVAssetResourceLoaderDelegate`.

   >[!IMPORTANT] {importance=&quot;high&quot;}
   >
   >Dans le scénario du serveur de licences ExpressPlay, pour lire le contenu, modifiez le modèle d’URL dans l’URL de demande de licence du serveur ExpressPlay FairPlay de `skd://` à `https://` (ou `https://`).

1. Enregistrez le chargeur de ressources client *FairPlay* avec `registerPTAVAssetResourceLoader`.

   ```
   PTFairPlayResourceLoader *resourceLoader =  
     [[PTFairPlayResourceLoader new] autorelease];  
   [[PTDefaultMediaPlayerClientFactory defaultFactory]  
     registerPTAVAssetResourceLoader:resourceLoader];
   ```

Si vous avez écrit votre propre serveur de licences FairPlay ou si vous utilisez un serveur de licences FairPlay tiers, consultez le fournisseur de votre serveur de licences pour déterminer l’URL, le formatage et toute autre exigence de votre serveur de licences.