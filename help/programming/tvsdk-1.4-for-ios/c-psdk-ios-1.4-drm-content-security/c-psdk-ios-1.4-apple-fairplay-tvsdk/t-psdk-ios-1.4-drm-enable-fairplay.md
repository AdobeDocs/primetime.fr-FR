---
description: Vous pouvez mettre en oeuvre Apple FairPlay Streaming, qui est une solution DRM Apple, dans vos applications TVSDK.
title: Activer Apple FairPlay dans les applications TVSDK
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# Activer Apple FairPlay dans les applications TVSDK{#enable-apple-fairplay-in-tvsdk-applications}

Vous pouvez mettre en oeuvre Apple FairPlay Streaming, qui est une solution DRM Apple, dans vos applications TVSDK.

1. Créez votre chargeur de ressources client FairPlay en implémentant `PTAVAssetResourceLoaderDelegate`.

   Pour plus d’informations, voir [Apple FairPlay dans les applications TVSDK](../../c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md).

   >[!NOTE]
   >
   >Veillez à suivre les instructions de la section *Guide du programme de diffusion en continu FairPlay* ( *FairPlayStreaming_PG.pdf*), qui est inclus dans [SDK du serveur FairPlay pour le développement d’une application tenant compte de FPS](https://developer.apple.com/services-account/download?path=/Developer_Tools/FairPlay_Streaming_SDK/FairPlay_Streaming_Server_SDK.zip)).

   La variable `resourceLoader:shouldWaitForLoadingOfRequestedResource` équivaut à ce qui se trouve dans `AVAssetResourceLoaderDelegate`.

   >[!IMPORTANT]
   >
   >Dans le scénario du serveur de licences ExpressPlay , pour lire le contenu, modifiez le modèle d’URL dans l’URL de demande de licence de serveur ExpressPlay à partir de `skd://` to `https://` (ou `https://`).

1. Enregistrez le *FairPlay* Customer Resource Loader avec `registerPTAVAssetResourceLoader`.

   ```
   PTFairPlayResourceLoader *resourceLoader =  
     [[PTFairPlayResourceLoader new] autorelease];  
   [[PTDefaultMediaPlayerClientFactory defaultFactory]  
     registerPTAVAssetResourceLoader:resourceLoader];
   ```

Si vous avez écrit votre propre serveur de licences FairPlay ou si vous utilisez un serveur de licences FairPlay tiers, consultez le fournisseur de votre serveur de licences pour déterminer l’URL, le formatage et toute autre exigence de votre serveur de licences.
