---
description: Vous pouvez mettre en oeuvre le module de diffusion en flux continu Apple FairPlay, qui est la solution DRM d’Apple, dans vos applications TVSDK.
seo-description: Vous pouvez mettre en oeuvre le module de diffusion en flux continu Apple FairPlay, qui est la solution DRM d’Apple, dans vos applications TVSDK.
seo-title: Activation d’Apple FairPlay dans les applications TVSDK
title: Activation d’Apple FairPlay dans les applications TVSDK
uuid: fafffdb9-09f9-45fb-9957-3c6e95ed55f9
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---


# Activer Apple FairPlay dans les applications TVSDK{#enable-apple-fairplay-in-tvsdk-applications}

Vous pouvez mettre en oeuvre le module de diffusion en flux continu Apple FairPlay, qui est la solution DRM d’Apple, dans vos applications TVSDK.

1. Créez votre chargeur de ressources client FairPlay en implémentant `PTAVAssetResourceLoaderDelegate`.

   Pour plus d’informations, voir [Apple FairPlay dans les applications TVSDK](../../c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md).

   >[!NOTE]
   >
   >Assurez-vous de suivre les instructions du *Guide du Programme de diffusion en flux continu FairPlay* ( *FairPlayStreaming_PG.pdf*), qui est inclus dans le [SDK du serveur FairPlay pour le développement d’une application compatible FPS](https://developer.apple.com/services-account/download?path=/Developer_Tools/FairPlay_Streaming_SDK/FairPlay_Streaming_Server_SDK.zip)).

   La méthode `resourceLoader:shouldWaitForLoadingOfRequestedResource` est équivalente à celle de `AVAssetResourceLoaderDelegate`.

   >[!IMPORTANT]
   >
   >Dans le scénario du serveur de licences ExpressPlay, pour lire le contenu, modifiez le modèle d’URL dans l’URL de demande de licence de serveur ExpressPlay FairPlay de `skd://` à `https://` (ou `https://`).

1. Enregistrez le chargeur de ressources client *FairPlay* avec `registerPTAVAssetResourceLoader`.

   ```
   PTFairPlayResourceLoader *resourceLoader =  
     [[PTFairPlayResourceLoader new] autorelease];  
   [[PTDefaultMediaPlayerClientFactory defaultFactory]  
     registerPTAVAssetResourceLoader:resourceLoader];
   ```

Si vous écrivez votre propre serveur de licences FairPlay ou si vous utilisez un serveur de licences FairPlay tiers, consultez le fournisseur de votre serveur de licences pour déterminer l’URL, la mise en forme et d’autres exigences de votre serveur de licences.
