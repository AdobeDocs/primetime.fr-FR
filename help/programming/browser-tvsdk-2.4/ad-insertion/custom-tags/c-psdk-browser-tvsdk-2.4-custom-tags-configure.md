---
description: Les diffusions multimédia peuvent comporter des métadonnées supplémentaires sous la forme de balises dans le fichier MPD (Media Presentation Description), et ce fichier indique l’emplacement de la publicité. Vous pouvez spécifier des noms de balise personnalisés et être averti lorsque certaines balises apparaissent dans le fichier de manifeste.
title: Balises personnalisées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Présentation {#custom-tags-overview}

Les diffusions multimédia peuvent comporter des métadonnées supplémentaires sous la forme de balises dans le fichier MPD (Media Presentation Description), et ce fichier indique l’emplacement de la publicité. Vous pouvez spécifier des noms de balise personnalisés et être averti lorsque certaines balises apparaissent dans le fichier de manifeste.

## Balises de contenu HLS {#section_E99299152089418FBA56F5F09FC547B0}

>[!IMPORTANT]
>
>Cette fonctionnalité n’est pas disponible pour Safari sur les ordinateurs Apple, car le navigateur TVSDK utilise la balise vidéo, plutôt que Flash ou MSE, pour lire le contenu HLS.

Le navigateur TVSDK fournit une prise en charge prête à l’emploi de balises publicitaires #EXT spécifiques. Votre application peut utiliser des balises personnalisées pour améliorer le workflow publicitaire ou pour prendre en charge les scénarios de blackout. Pour prendre en charge les workflows avancés, le Browser TVSDK vous permet de spécifier et d’abonner des balises supplémentaires dans le manifeste. Vous pouvez être averti lorsque ces balises apparaissent dans le fichier de manifeste.

>[!TIP]
>
>Vous pouvez vous abonner à des balises personnalisées pour les flux VOD et les flux live/linéaires.

>[!NOTE]
>
>Lorsque HLS est lu en utilisant la balise Vidéo dans Safari, et non en utilisant Flash Fallback, cette fonctionnalité n’est pas disponible dans Safari.

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

* Une notification lorsque `#EXT-X-ASSET` des balises, ou tout autre ensemble de noms de balises personnalisés auxquels vous vous êtes abonné, existent dans le fichier .
* Insérer des publicités lorsqu’une `#EXT-X-AD` La balise , ou tout autre nom de balise personnalisé, se trouve dans le flux.

Vous pouvez vous abonner à l’une des balises personnalisées suivantes : `EXT-PROGRAM-DATE-TIME`, `EXT-X-START`, `EXT-X-AD`, `EXT-X-CUE`, `EXT-X-ENDLIST`. Vous êtes averti par une `TimedMetadata` lors de l’analyse des fichiers manifest.

Il existe certaines balises publicitaires, telles que `EXT-X-CUE`, auquel vous êtes déjà abonné. Ces balises publicitaires sont également utilisées par le générateur d’opportunités par défaut. Vous pouvez spécifier les balises d’annonce utilisées par le générateur d’opportunités par défaut en définissant la variable `adTags` .

## Balises de contenu DASH {#section_967A952319BE4048B4C6612FFF7ADA6E}

DASH propose deux méthodes de signalétique des événements :

* Dans le fichier MPD.

  Ce fichier est similaire au fichier M3U8 dans le contenu HLS et les événements MPD existent dans le fichier .mpd.
* Incorporer dans la représentation

  Les événements intrabande sont multiplexés avec des représentations en ajoutant les messages d’événement dans le cadre des segments. Une représentation est une liste des segments vidéo et audio lus en séquence. Les données d’événement intégrées sont incorporées dans ces segments.

Ces événements sont avertis en tant que `TimedMetadata` à l’application dès qu’elles sont analysées par Browser TVSDK. Une fois qu’un événement est averti, il ne sera plus averti.
