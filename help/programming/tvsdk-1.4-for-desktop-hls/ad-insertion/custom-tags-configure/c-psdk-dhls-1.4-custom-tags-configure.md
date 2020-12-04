---
description: Les flux de médias peuvent contenir des métadonnées supplémentaires sous la forme de balises dans le fichier playlist/manifest, et ce fichier indique l’emplacement de la publicité. Vous pouvez spécifier des noms de balises personnalisés et être averti lorsque certaines balises apparaissent dans le fichier manifeste.
seo-description: Les flux de médias peuvent contenir des métadonnées supplémentaires sous la forme de balises dans le fichier playlist/manifest, et ce fichier indique l’emplacement de la publicité. Vous pouvez spécifier des noms de balises personnalisés et être averti lorsque certaines balises apparaissent dans le fichier manifeste.
seo-title: Balises personnalisées
title: Balises personnalisées
uuid: 648645c8-f7cc-4118-b169-cc5c473afe23
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# Balises personnalisées{#custom-tags}

Les flux de médias peuvent contenir des métadonnées supplémentaires sous la forme de balises dans le fichier playlist/manifest, et ce fichier indique l’emplacement de la publicité. Vous pouvez spécifier des noms de balises personnalisés et être averti lorsque certaines balises apparaissent dans le fichier manifeste.

## Balises de contenu HLS {#section_E99299152089418FBA56F5F09FC547B0}

>[!IMPORTANT]
>
>Cette fonctionnalité n’est pas disponible pour Safari sur les ordinateurs Apple, car TVSDK utilise la balise vidéo, plutôt que le Flash ou le MSE, pour lire le contenu HLS.

TVSDK fournit un support prêt à l’emploi pour des balises publicitaires #EXT spécifiques. Votre application peut utiliser des balises personnalisées pour améliorer le processus publicitaire ou pour prendre en charge les scénarios de coupure de courant. Pour prendre en charge les workflows avancés, TVSDK vous permet de spécifier et d’abonner des balises supplémentaires dans le manifeste. Vous pouvez être averti lorsque ces balises apparaissent dans le fichier manifeste.

>[!TIP]
>
>Vous pouvez vous abonner à des balises personnalisées pour les flux VOD et les flux dynamiques/linéaires.

>[!NOTE]
>
>Lorsque HLS est lu en utilisant la balise Vidéo dans Safari, et non en utilisant Flash Fallback, cette fonctionnalité ne sera pas disponible dans Safari.

## Utilisation de balises HLS personnalisées {#section_AD032318AEF5418393D2B1DF36B0BABB}

Voici un exemple de ressource VOD personnalisée :

```
#EXTM3U
#EXT-X-VERSION:3
#EXT-X-TARGETDURATION:7
 
#EXT-X-ASSET:AID=10
 
#EXTINF:9.9766,
seg1.ts
 
#EXTINF:9.9766,
seg2.ts
 
#EXTINF:9.9766,
seg3.ts
 
#EXT-X-AD:DURATION=10
#EXTINF:9.9766,
seg4.ts
 
#EXTINF:9.9766,
seg5.ts
 
#EXT-X-ENDLIST
```

Votre application peut configurer les scénarios suivants :

* Une notification indiquant si des balises `#EXT-X-ASSET`, ou tout autre ensemble de noms de balises personnalisés auquel vous vous êtes abonné, existent dans le fichier.
* Insérez des publicités lorsqu’une balise `#EXT-X-AD` ou tout autre nom de balise personnalisé se trouve dans le flux.

Vous pouvez vous abonner à l’une des balises suivantes en tant que balises personnalisées : `EXT-PROGRAM-DATE-TIME`, `EXT-X-START`, `EXT-X-AD`, `EXT-X-CUE`, `EXT-X-ENDLIST`. Vous êtes averti avec un événement `TimedMetadata` lors de l&#39;analyse des fichiers de manifeste.

Il existe des balises publicitaires, telles que `EXT-X-CUE`, auxquelles vous êtes déjà abonné. Ces balises publicitaires sont également utilisées par le générateur d’opportunités par défaut. Vous pouvez spécifier les balises publicitaires utilisées par le générateur d&#39;opportunités par défaut en définissant la propriété `adTags`.
