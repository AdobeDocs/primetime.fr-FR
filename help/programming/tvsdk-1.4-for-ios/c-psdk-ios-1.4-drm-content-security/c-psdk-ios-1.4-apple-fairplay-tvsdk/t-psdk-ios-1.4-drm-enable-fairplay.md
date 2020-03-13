---
description: Vous pouvez mettre en oeuvre la diffusion en flux continu FairPlay d’Apple, qui est la solution DRM d’Apple, dans vos applications TVSDK.
seo-description: Vous pouvez mettre en oeuvre la diffusion en flux continu FairPlay d’Apple, qui est la solution DRM d’Apple, dans vos applications TVSDK.
seo-title: Activation d’Apple FairPlay dans les applications TVSDK
title: Activation d’Apple FairPlay dans les applications TVSDK
uuid: fafffdb9-09f9-45fb-9957-3c6e95ed55f9
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Activation d’Apple FairPlay dans les applications TVSDK{#enable-apple-fairplay-in-tvsdk-applications}

Vous pouvez mettre en oeuvre la diffusion en flux continu FairPlay d’Apple, qui est la solution DRM d’Apple, dans vos applications TVSDK.

1. Créez votre chargeur de ressources client FairPlay en implémentant `PTAVAssetResourceLoaderDelegate`.

   Pour plus d’informations, voir [Apple FairPlay dans les applications](../../c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md)TVSDK.

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
