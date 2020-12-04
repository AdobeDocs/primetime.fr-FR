---
description: TVSDK a des exigences spécifiques pour le contenu multimédia, le contenu manifeste, la gestion des droits numériques et les versions logicielles.
seo-description: TVSDK a des exigences spécifiques pour le contenu multimédia, le contenu manifeste, la gestion des droits numériques et les versions logicielles.
seo-title: Conditions requises
title: Conditions requises
uuid: aa51fb78-31d1-4403-8808-2d54a87f6153
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Exigences {#requirements}

TVSDK a des exigences spécifiques pour le contenu multimédia, le contenu manifeste, la gestion des droits numériques et les versions logicielles.

## Configuration système et logiciel requise {#section_96E5B079900246E78682AE44D3F23068}

Pour utiliser TVSDK, assurez-vous que les versions de votre matériel, de votre système d’exploitation et de votre application répondent toutes aux exigences minimales énumérées ci-dessous.

| Système d’exploitation | Android 4.0 ou version ultérieure (niveau d’API minimal 14) |
|---|---|
| CPU | 1 GHz simple coeur ou équivalent |
| RAM | 256 Mo |
| GPU | GPU matériel requis pour la lecture |
| Architecture | x86 via Houdini, ARM64, ARMv7 et ARMv8 |

## Exigences en matière de contenu et de manifeste {#section_72DD0E4DA9774DCCADB42887497F1386}

Vérifiez les restrictions et les exigences relatives aux flux et aux listes de lecture (manifestes), y compris les clés de chiffrement DRM.

| DRM d&#39;accès Adobe | Si le flux protégé par DRM est à débit multiple (MBR), la clé de chiffrement DRM utilisée pour le MBR doit être identique à la clé utilisée dans tous les flux de débit binaire. |
|---|---|
| Manifestations de variantes d&#39;annonce | Doit avoir les mêmes rendus de débit que les rendus du contenu principal. |

## #EXT-X-VERSION requirements {#section_49A33664651A46EC9ED888BA9C1C3F6D}

La version de `#EXT-X-VERSION` dans le fichier manifeste [!DNL .m3u8] affecte les fonctionnalités disponibles pour votre application et les balises `EXT` valides.

Voici quelques informations sur la balise `#EXT-X-VERSION`, qui spécifie la version du protocole HLS :

* La version doit correspondre aux fonctionnalités et aux attributs de la liste de lecture HLS ; sinon, des erreurs de lecture peuvent se produire. Pour plus d’informations, voir [HTTP Live Streaming Specification](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1).
* Adobe recommande d’utiliser au moins la version 2 de HLS pour la lecture sur les clients basés sur TVSDK.

   Les clients et les serveurs doivent implémenter les versions de la manière suivante :

<table frame="all" colsep="1" rowsep="1" id="table_62EB98EDD9DE49EC84CB1C7D59BC40E6"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Utiliser au moins cette version </th> 
   <th colname="2" class="entry"> Pour utiliser ces fonctionnalités </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:2  </span> </td> 
   <td colname="2"> Attribut IV de la balise <span class="codeph"> EXT-X-KEY </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3  </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Valeurs de durée de point flottant <span class="codeph"> EXTINF </span> <p>Les balises de durée ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) dans la version 2 ont été arrondis à des valeurs entières. Les versions 3 et ultérieures nécessitent des durées précises, en virgule flottante. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:4  </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_5E73D41AF6DC4CEE88D6C029FFCFC350">La balise <span class="codeph"> EXT-X-BYTERANGE </span> </li> 
     <li id="li_BF5141F516F749E5890860D487EB5287">La balise <span class="codeph"> EXT-X-I-FRAME-STREAM-INF </span> </li> 
     <li id="li_E0D399A13812499B94107CDE62998EE9">La balise <span class="codeph"> EXT-X-I-FRAMES-ONLY </span> </li> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">La balise <span class="codeph"> EXT-X-MEDIA </span> </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">Les attributs <span class="codeph"> AUDIO </span> et <span class="codeph"> VIDEO </span> de la balise <span class="codeph"> EXT-X-STREAM-INF </span> </li> 
     <li id="li_DB2A7847D5884F6E91FD9E78101FBCA5">Audio alternatif TVSDK </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>