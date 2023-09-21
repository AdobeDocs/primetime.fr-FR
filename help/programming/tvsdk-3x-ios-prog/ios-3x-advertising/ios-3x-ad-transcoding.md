---
description: Certaines publicités tierces (ou créatives) ne peuvent pas être regroupées dans le flux de contenu HTTP Live Streaming (HLS), car leur format vidéo est incompatible avec HLS. L’insertion de publicités Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles dans des vidéos compatibles M3U8.
title: Recompressez les publicités incompatibles à l’aide du service Adobe Creative Repackaging
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Recompressez les publicités incompatibles à l’aide du service Adobe Creative Repackaging {#repackage-incompatible-ads-using-adobe-creative-repackaging-service}

Certaines publicités tierces (ou créatives) ne peuvent pas être regroupées dans le flux de contenu HTTP Live Streaming (HLS), car leur format vidéo est incompatible avec HLS. L’insertion de publicités Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles dans des vidéos compatibles M3U8.

Les publicités diffusées par des tiers, tels qu’un serveur de publicités d’agence, votre partenaire d’inventaire ou un réseau publicitaire, sont souvent diffusées dans des formats incompatibles, tels que le téléchargement progressif MP4.

Lorsque TVSDK rencontre pour la première fois une publicité incompatible, le lecteur ignore la publicité et émet une demande au service de reconditionnement de création (CRS), qui fait partie du serveur principal d’insertion de publicités Primetime, afin de la recompresser dans un format compatible. CRS tente de générer des rendus M3U8 à débit multiple de la publicité et stocke ces rendus sur le réseau de diffusion de contenu (CDN) Primetime. La prochaine fois que TVSDK reçoit une réponse publicitaire pointant vers cette publicité, le lecteur utilise la version compatible HLS M3U8 du réseau de diffusion de contenu.

Pour activer cette fonction facultative, contactez votre représentant d’Adobe.

## Prise en charge de plusieurs CDN pour CRS et diffusion {#section_900FDDA5454143718F1EB4C9732C8E1C}

Bien que le scénario par défaut de Creative Repackaging Service (CRS) consiste à utiliser un réseau de données de contenu (CDN), vous pouvez déployer des ressources CRS sur plusieurs réseaux CDN.

Vous pouvez utiliser plusieurs CDN pour les raisons suivantes :

* Obligation de dimensionner les événements de visionnage de grande taille.
* Une exigence pour faire correspondre la source CDN de la ressource CRS à la source CDN du contenu principal.

Vous pouvez transformer l’URL par défaut fournie par CRS en utilisant les API TVSDK URL Transformer.

Voici les ajouts d’API dans TVSDK :

* `PTURLTransformer` Protocole qui décrit les méthodes requises pour transformer les URL et CRS demandées par TVSDK. Les applications peuvent implémenter ce protocole et fournir des mises en oeuvre pour les méthodes requises.

* `PTDefaultURLTransformer` L’instance du transformateur d’URL par défaut créée dans TVSDK et qui met en oeuvre le `PTURLTransformer` protocole . Les applications peuvent remplacer cette classe ou ajouter un gestionnaire de transformation post URL. Ce gestionnaire est utile lorsque l’application souhaite apporter des modifications à la requête d’URL après l’application de la transformation par défaut.

* `PTNetworkConfiguration setURLTransformer:defaultTransformer` Une méthode setter fournie sur la variable `PTNetworkConfiguration` instance de métadonnées pour définir la variable `PTURLTransformer` implémentation.

>[!IMPORTANT]
>
>Les mises en oeuvre de votre application doivent rechercher la variable `PTURLTransformerInputType` énumération et ne transformer que les URL de type `PTURLTransformerInputTypeCRSCreative` pour CRS.

L’exemple de code suivant montre comment votre application peut remplacer le composant hôte par défaut par une autre chaîne (par exemple : `cdn.mycrsdomain.com`) :

```
// The sample code below uses Non-ARC code 
PTNetworkConfiguration *networkConfiguration = [[[PTNetworkConfiguration alloc] init] autorelease]; 
   
PTDefaultURLTransformer *defaultTransformer = [[[PTDefaultURLTransformer alloc] init] autorelease]; 
    [defaultTransformer addPostURLTransformHandler:^NSString *(NSString *url, PTURLTransformerInputType type) { 
        if (type == PTURLTransformerInputTypeCRSCreative) { 
            return [url stringByReplacingOccurrencesOfString:[NSURL URLWithString:url].host  
              withString:@"cdn.mycrsdomain.com"]; 
        } 
            return url; 
    }]; 
  
[networkConfiguration setURLTransformer:defaultTransformer]; 
   
// metadata is the PTMetadata instance set on a PTMediaPlayerItem instance. 
[metadata setMetadata:[self getNetworkConfiguration] forKey:PTNetworkConfigurationMetadataKey];
```
