---
description: Les flux de médias peuvent comporter des métadonnées supplémentaires sous la forme de balises dans le fichier playlist/manifest, et ce fichier indique l’emplacement de la publicité. Vous pouvez spécifier des noms de balises personnalisés et être averti lorsque certaines balises apparaissent dans le fichier manifeste.
seo-description: Les flux de médias peuvent comporter des métadonnées supplémentaires sous la forme de balises dans le fichier playlist/manifest, et ce fichier indique l’emplacement de la publicité. Vous pouvez spécifier des noms de balises personnalisés et être averti lorsque certaines balises apparaissent dans le fichier manifeste.
seo-title: Balises personnalisées
title: Balises personnalisées
uuid: 2892712f-bb01-4112-baee-6dcafd4fb923
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Présentation {#custom-tags-overview}

Les flux de médias peuvent comporter des métadonnées supplémentaires sous la forme de balises dans le fichier playlist/manifest, et ce fichier indique l’emplacement de la publicité. Vous pouvez spécifier des noms de balises personnalisés et être averti lorsque certaines balises apparaissent dans le fichier manifeste.

## Balises de contenu HLS {#section_E99299152089418FBA56F5F09FC547B0}

>[!IMPORTANT]
>
>Cette fonctionnalité n’est pas disponible pour Safari sur les ordinateurs Apple, car TVSDK utilise la balise vidéo, plutôt que Flash ou MSE, pour lire le contenu HLS.

TVSDK fournit une prise en charge prête à l’emploi de balises `#EXT` publicitaires spécifiques. Votre application peut utiliser des balises personnalisées pour améliorer le processus publicitaire ou pour prendre en charge les scénarios de coupure de courant. Pour prendre en charge les  avancées, TVSDK vous permet de spécifier et d’abonner des balises supplémentaires dans le manifeste. Vous pouvez être averti lorsque ces balises apparaissent dans le fichier manifeste.

>[!TIP]
>
>Vous pouvez vous abonner à des balises personnalisées pour les flux VOD et les flux dynamiques/linéaires.

>[!LIMITATION] {othertype=&quot;Limitation&quot;}
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

Vous pouvez vous abonner à l’une des balises suivantes sous forme de balises personnalisées :

* `EXT-PROGRAM-DATE-TIME`
* `EXT-X-START`
* `EXT-X-AD`
* `EXT-X-CUE`
* `EXT-X-ENDLIST`

Vous serez averti par un `TimedMetadata` lors de l&#39;analyse des fichiers de manifeste.

Il existe des balises publicitaires, telles que `EXT-X-CUE`, auxquelles vous êtes déjà abonné. Ces balises publicitaires sont également utilisées par le générateur d’opportunités par défaut. Vous pouvez spécifier les balises publicitaires utilisées par le générateur d’opportunités par défaut en définissant la `adTags` propriété.