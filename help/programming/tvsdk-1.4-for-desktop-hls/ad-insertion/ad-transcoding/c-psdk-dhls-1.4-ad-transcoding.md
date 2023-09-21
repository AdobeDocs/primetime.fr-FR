---
description: Certaines publicités tierces (ou créatives) ne peuvent pas être regroupées dans le flux de contenu HTTP Live Streaming (HLS), car leur format vidéo est incompatible avec HLS. L’insertion de publicités Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles dans des vidéos compatibles M3U8.
title: Recompressez les publicités incompatibles à l’aide du service Adobe Creative Repackaging
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Recompressez les publicités incompatibles à l’aide du service Adobe Creative Repackaging {#repackage-incompatible-ads-using-adobe-creative-repackaging-service}

Certaines publicités tierces (ou créatives) ne peuvent pas être regroupées dans le flux de contenu HTTP Live Streaming (HLS), car leur format vidéo est incompatible avec HLS. L’insertion de publicités Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles dans des vidéos compatibles M3U8.

Les publicités diffusées par des tiers, tels qu’un serveur de publicités d’agence, votre partenaire d’inventaire ou un réseau publicitaire, sont souvent diffusées dans des formats incompatibles, tels que le téléchargement progressif MP4.

Lorsque TVSDK rencontre pour la première fois une publicité incompatible, le lecteur ignore la publicité et émet une demande au service de reconditionnement de création (CRS), qui fait partie du serveur principal d’insertion de publicités Primetime, afin de la recompresser dans un format compatible. CRS tente de générer des rendus M3U8 à débit multiple de la publicité et stocke ces rendus sur le réseau de diffusion de contenu (CDN) Primetime. La prochaine fois que TVSDK reçoit une réponse publicitaire pointant vers cette publicité, le lecteur utilise la version compatible HLS M3U8 du réseau de diffusion de contenu.

Pour activer cette fonction facultative, contactez votre représentant d’Adobe.

Pour plus d’informations sur CRS, voir [Creative Packaging Service (CRS)](https://helpx.adobe.com/content/dam/help/en/primetime/guides/crs.pdf).

## Prise en charge de plusieurs CDN pour CRS et diffusion {#multiple-cdn-support-for-crs-ad-delivery}

Bien que le scénario par défaut de Creative Repackaging Service (CRS) consiste à utiliser un réseau de données de contenu (CDN), vous pouvez déployer des ressources CRS sur plusieurs réseaux CDN.

Vous pouvez utiliser plusieurs CDN pour les raisons suivantes :

* Obligation de dimensionner les événements de visionnage de grande taille.
* Une exigence pour faire correspondre la source CDN de la ressource CRS à la source CDN du contenu principal.

Vous pouvez transformer l’URL par défaut fournie par CRS en utilisant les API TVSDK URL Transformer.

Voici les ajouts d’API dans TVSDK :

* `URLTransformer` Interface qui décrit les méthodes requises pour transformer les URL et les CRS qui sont demandées par TVSDK. Les applications peuvent implémenter cette interface et fournir des implémentations pour les méthodes requises.

* `DefaultURLTransformer` L’instance du transformateur d’URL par défaut créée dans TVSDK et qui met en oeuvre le `URLTransformer` . Les applications peuvent remplacer cette classe ou ajouter un gestionnaire de transformation post URL. Ce gestionnaire est utile lorsque l’application souhaite apporter des modifications à la requête d’URL après l’application de la transformation par défaut.

* `NetworkConfiguration.urlTransformer` Une méthode setter fournie sur la variable `NetworkConfiguration` instance de métadonnées pour définir la variable `URLTransformer` implémentation.

>[!IMPORTANT]
>
>Les mises en oeuvre de votre application doivent rechercher la variable `URLTransformerInputType` énumération et ne transformer que les URL de type `URLTransformerInputType.CRSCreative` pour CRS.

L’exemple de code suivant montre comment votre application peut remplacer le composant hôte par défaut par une autre chaîne (par exemple : `cdn.mycrsdomain.com`) :

```
var networkConfiguration:NetworkConfiguration = new NetworkConfiguration(); 
   
var urlTransformer:DefaultURLTransformer = new DefaultURLTransformer(); 
urlTransformer.addPostURLTransformHandler(function (url:String, type:String) { 
    if (type == URLTransformerInputType.CRSCreative) { 
        return url.replace(URLUtil.getServerName(url), "cdn.mycrsdomain.com"); 
    } 
    return url; 
}); 
  
networkConfiguration.urlTransformer = urlTransformer; 
   
// metadata is the Metadata instance set on a MediaResource instance. 
metadata.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                     networkConfiguration);
```
