---
description: Certaines publicités (ou créatives) tierces ne peuvent pas être assemblées dans le flux de contenu HLS (HTTP Live Streaming), car leur format vidéo est incompatible avec HLS. L’insertion d’annonces Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles en vidéos compatibles M3U8.
title: Réparer les publicités incompatibles à l’aide du service de reconditionnement Creative Adobe
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---


# Réparer les publicités incompatibles à l&#39;aide du service de reconditionnement créatif d&#39;Adobe {#repackage-incompatible-ads-using-adobe-creative-repackaging-service}

Certaines publicités (ou créatives) tierces ne peuvent pas être assemblées dans le flux de contenu HLS (HTTP Live Streaming), car leur format vidéo est incompatible avec HLS. L’insertion d’annonces Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles en vidéos compatibles M3U8.

Les publicités diffusées par divers tiers, tels qu’un serveur d’annonces d’agence, votre partenaire d’inventaire ou un réseau publicitaire, sont souvent diffusées dans des formats incompatibles, tels que MP4 à téléchargement progressif.

Lorsque TVSDK rencontre pour la première fois une publicité incompatible, le lecteur ignore la publicité et envoie une demande au service de reconditionnement de la création (CRS), qui fait partie du serveur principal Primetime et d’insertion, afin de reconditionner la publicité dans un format compatible. CRS tente de générer des rendus M3U8 à débit multiple de la publicité et stocke ces rendus sur le réseau de Diffusion de contenu Primetime (CDN). La prochaine fois que TVSDK recevra une réponse publicitaire pointant vers cette publicité, le lecteur utilisera la version compatible HLS M3U8 du CDN.

Pour activer cette fonctionnalité facultative, contactez votre représentant d’Adobe.

Pour plus d&#39;informations sur CRS, voir [Creative Packaging Service (CRS)](https://helpx.adobe.com/content/dam/help/en/primetime/guides/crs.pdf).

## Prise en charge de plusieurs CDN pour CRS et diffusion {#multiple-cdn-support-for-crs-ad-delivery}

Bien que le scénario par défaut de Creative Repackaging Service (CRS) consiste à utiliser un réseau de données de contenu (CDN), vous pouvez déployer des ressources CRS sur plusieurs CDN.

Vous pouvez utiliser plusieurs CDN pour les raisons suivantes :

* Configuration requise pour l’agrandissement des événements d’affichage de grande taille.
* Obligation de faire correspondre la source CDN du fichier CRS à la source CDN du contenu principal.

Vous pouvez transformer l’URL par défaut fournie par CRS en utilisant les API de transformation d’URL TVSDK.

Voici les ajouts d’API dans TVSDK :

* `URLTransformer` Interface décrivant les méthodes nécessaires à la transformation des fichiers CRS et des URL demandés par TVSDK. Les applications peuvent implémenter cette interface et fournir des implémentations pour les méthodes requises.

* `DefaultURLTransformer` Instance de transformateur d’URL par défaut créée dans TVSDK et qui implémente l’ `URLTransformer` interface. Les applications peuvent remplacer cette classe ou ajouter un gestionnaire de transformation post URL. Ce gestionnaire est utile lorsque l’application souhaite apporter des modifications à la demande d’URL après l’application de la transformation par défaut.

* `NetworkConfiguration.urlTransformer` Méthode setter fournie sur l’instance de  `NetworkConfiguration` métadonnées pour définir l’ `URLTransformer` implémentation.

>[!IMPORTANT]
>
>Les implémentations de votre application doivent rechercher la énumération `URLTransformerInputType` et uniquement transformer les URL de type `URLTransformerInputType.CRSCreative` pour CRS.

L&#39;exemple de code suivant montre comment votre application peut changer le composant hôte par défaut en une autre chaîne (par exemple, `cdn.mycrsdomain.com`) :

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
