---
description: Certaines publicités (ou créatives) tierces ne peuvent pas être assemblées dans le flux de contenu HLS (HTTP Live Streaming), car leur format vidéo est incompatible avec HLS. L’insertion d’annonces Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles en vidéos compatibles M3U8.
seo-description: Certaines publicités (ou créatives) tierces ne peuvent pas être assemblées dans le flux de contenu HLS (HTTP Live Streaming), car leur format vidéo est incompatible avec HLS. L’insertion d’annonces Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles en vidéos compatibles M3U8.
seo-title: Réparer les publicités incompatibles à l’aide du service de reconditionnement Creative Adobe
title: Réparer les publicités incompatibles à l’aide du service de reconditionnement Creative Adobe
uuid: e8be1ed2-3ee3-4ee7-a75c-b804ab398568
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---


# Réparer les publicités incompatibles à l’aide d’Adobe Creative Repackaging Service{#repackage-incompatible-ads-using-adobe-creative-repackaging-service}

Certaines publicités (ou créatives) tierces ne peuvent pas être assemblées dans le flux de contenu HLS (HTTP Live Streaming), car leur format vidéo est incompatible avec HLS. L’insertion d’annonces Primetime et TVSDK peuvent éventuellement tenter de recompresser des publicités incompatibles en vidéos compatibles M3U8.

Les publicités diffusées par divers tiers, tels qu’un serveur d’annonces d’agence, votre partenaire d’inventaire ou un réseau publicitaire, sont souvent diffusées dans des formats incompatibles, tels que MP4 à téléchargement progressif.

Lorsque TVSDK rencontre pour la première fois une publicité incompatible, le lecteur ignore la publicité et envoie une demande au service de reconditionnement de la création (CRS), qui fait partie du serveur principal Primetime et d’insertion, afin de reconditionner la publicité dans un format compatible. CRS tente de générer des rendus M3U8 à débit multiple de la publicité et stocke ces rendus sur le réseau de Diffusion de contenu Primetime (CDN). La prochaine fois que TVSDK recevra une réponse publicitaire pointant vers cette publicité, le lecteur utilisera la version compatible HLS M3U8 du CDN.

Pour activer cette fonctionnalité facultative, contactez votre représentant d’Adobe.

Pour plus d&#39;informations sur CRS, voir [Creative Packaging Service (CRS)](https://helpx.adobe.com/content/dam/help/en/primetime/guides/crs.pdf).

## Prise en charge de plusieurs CDN pour CRS et diffusion {#section_900FDDA5454143718F1EB4C9732C8E1C}

Bien que le scénario par défaut de Creative Repackaging Service (CRS) consiste à utiliser un réseau de données de contenu (CDN), vous pouvez déployer des ressources CRS sur plusieurs CDN.

Vous pouvez utiliser plusieurs CDN pour les raisons suivantes :

* Configuration requise pour l’agrandissement des événements d’affichage de grande taille.
* Obligation de faire correspondre la source CDN du fichier CRS à la source CDN du contenu principal.

Vous pouvez transformer l’URL par défaut fournie par CRS en utilisant les API de transformation d’URL TVSDK.

Voici les ajouts d’API dans TVSDK :

* `PTURLTransformer` Protocole décrivant les méthodes requises pour transformer les CRS et les URL demandées par TVSDK. Les applications peuvent implémenter ce protocole et fournir des implémentations pour les méthodes requises.

* `PTDefaultURLTransformer` Instance de transformateur d’URL par défaut créée dans TVSDK et qui implémente le  `PTURLTransformer` protocole. Les applications peuvent remplacer cette classe ou ajouter un gestionnaire de transformation post URL. Ce gestionnaire est utile lorsque l’application souhaite apporter des modifications à la demande d’URL après l’application de la transformation par défaut.

* `PTNetworkConfiguration setURLTransformer:defaultTransformer` Méthode setter fournie sur l’instance de  `PTNetworkConfiguration` métadonnées pour définir l’ `PTURLTransformer` implémentation.

>[!IMPORTANT]
>
>Les implémentations de votre application doivent rechercher la énumération `PTURLTransformerInputType` et uniquement transformer les URL de type `PTURLTransformerInputTypeCRSCreative` pour CRS.

L&#39;exemple de code suivant montre comment votre application peut changer le composant hôte par défaut en une autre chaîne (par exemple, `cdn.mycrsdomain.com`) :

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

