---
description: L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer la charge de manière plus efficace.
seo-description: L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer la charge de manière plus efficace.
seo-title: Optimisation de la redirection HTTP 302
title: Optimisation de la redirection HTTP 302
uuid: 4bee0555-ae46-47c1-a067-206ad7ca8883
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 1%

---


# Optimisation de la redirection HTTP 302 {#http-redirect-optimization}

L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer la charge de manière plus efficace.

Si une requête de manifeste principale est redirigée et que l’optimisation de la version 302 est activée dans votre lecteur, les requêtes suivantes effectuées pour les ressources à partir de ce manifeste utiliseront l’emplacement de domaine final, ce qui évite 302 réponses supplémentaires. Cette fonction est activée par défaut et vous pouvez modifier ce paramètre.

## Désactivation ou activation de l&#39;optimisation de la redirection 302 {#section_8977448B268E41D69A8F75B60EB9DA3B}

Utilisez la propriété `useRedirectedUrl` pour activer la redirection 302 ( `true`) ou la désactiver ( `false`).

<!--<a id="example_888749F70C8A43279D06A29BD68E7E4D"></a>-->

Par exemple :

```java
// Set useRedirectedUrl property to false 
NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
networkConfiguration.setUseRedirectedUrl(false); 
 
//Set NetworkConfiguration on MediaPlayerItemConfig 
MediaPlayerItemConfig config = new MediaPlayerItemConfig (); 
config.setNetworkConfiguration(networkConfiguration); 
 
//Use this config when loading the MediaPlayerItem or calling replaceCurrentResource
```

