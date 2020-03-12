---
description: Les flux de médias peuvent comporter des métadonnées supplémentaires sous la forme de balises dans le fichier de description de la présentation multimédia (MPD), et ce fichier indique l’emplacement de la publicité. Vous pouvez spécifier des noms de balises personnalisés et être averti lorsque certaines balises apparaissent dans le fichier manifeste.
seo-description: Les flux de médias peuvent comporter des métadonnées supplémentaires sous la forme de balises dans le fichier de description de la présentation multimédia (MPD), et ce fichier indique l’emplacement de la publicité. Vous pouvez spécifier des noms de balises personnalisés et être averti lorsque certaines balises apparaissent dans le fichier manifeste.
seo-title: Balises personnalisées
title: Balises personnalisées
uuid: d1e34288-545b-440f-a262-2fb853f0e3c4
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Présentation {#custom-tags-overview}

Les flux de médias peuvent comporter des métadonnées supplémentaires sous la forme de balises dans le fichier de description de la présentation multimédia (MPD), et ce fichier indique l’emplacement de la publicité. Vous pouvez spécifier des noms de balises personnalisés et être averti lorsque certaines balises apparaissent dans le fichier manifeste.

## Balises de contenu HLS {#section_E99299152089418FBA56F5F09FC547B0}

>[!IMPORTANT]
>
>Cette fonctionnalité n’est pas disponible pour Safari sur les ordinateurs Apple, car le navigateur TVSDK utilise la balise vidéo, plutôt que Flash ou MSE, pour lire le contenu HLS.

Le navigateur TVSDK fournit une prise en charge prête à l’emploi de balises publicitaires #EXT spécifiques. Votre application peut utiliser des balises personnalisées pour améliorer le processus publicitaire ou pour prendre en charge les scénarios de coupure de courant. Pour prendre en charge les  avancées, le navigateur TVSDK vous permet de spécifier et d’abonner des balises supplémentaires dans le manifeste. Vous pouvez être averti lorsque ces balises apparaissent dans le fichier manifeste.

>[!TIP]
>
>Vous pouvez vous abonner à des balises personnalisées pour les flux VOD et les flux dynamiques/linéaires.

>[!NOTE] {othertype=&quot;Limitation&quot;}
>
>Lorsque HLS est lu à l’aide de la balise Vidéo dans Safari, et non à l’aide de Flash Fallback, cette fonctionnalité n’est pas disponible dans Safari.

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

* Une notification lorsque `#EXT-X-ASSET` des balises, ou tout autre jeu de noms de balises personnalisées auquel vous vous êtes abonné, existent dans le fichier.
* Insérez des publicités lorsqu’une `#EXT-X-AD` balise, ou tout autre nom de balise personnalisé, se trouve dans le flux.

Vous pouvez vous abonner à l’une des balises suivantes sous forme de balises personnalisées : `EXT-PROGRAM-DATE-TIME`, `EXT-X-START`, `EXT-X-AD`, `EXT-X-CUE`, `EXT-X-ENDLIST`. Vous êtes averti par un `TimedMetadata` lors de l’analyse des fichiers de manifeste.

Il existe des balises publicitaires, telles que `EXT-X-CUE`, auxquelles vous êtes déjà abonné. Ces balises publicitaires sont également utilisées par le générateur d’opportunités par défaut. Vous pouvez spécifier les balises publicitaires utilisées par le générateur d’opportunités par défaut en définissant la `adTags` propriété.

## Balises de contenu DASH {#section_967A952319BE4048B4C6612FFF7ADA6E}

La DASH a deux façons de signaler les  :

* Dans le fichier MPD.

   Ce fichier est similaire au fichier M3U8 dans le contenu HLS et le MPD existe dans le fichier .mpd.
* Intérieur dans la représentation

   Les  en bande sont multiplexés avec des représentations en ajoutant les messages de  dans le cadre des segments. Une représentation est un  de segments vidéo et audio lus en séquence. Les données  du intégré sont intégrées à ces segments.

Ces  sont avertis en tant que `TimedMetadata` à l’application dès qu’ils sont analysés par le navigateur TVSDK. Une fois qu&#39;un est averti, il ne sera plus averti.
