---
description: TVSDK comporte des exigences spécifiques pour le contenu multimédia, le contenu manifeste, la gestion des droits numériques et les versions logicielles.
title: Conditions
exl-id: 85bf7b85-5f4b-4ed5-aa4f-765dabc5d4d8
source-git-commit: 3b051c3188c81673129e12dfeb573aaf85c15c97
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Conditions {#requirements}

TVSDK comporte des exigences spécifiques pour le contenu multimédia, le contenu manifeste, la gestion des droits numériques et les versions logicielles.

## Configuration requise et logiciels {#section_96E5B079900246E78682AE44D3F23068}

Pour utiliser TVSDK, assurez-vous que les versions de votre matériel, de votre système d’exploitation et de vos applications répondent toutes aux exigences minimales répertoriées ci-dessous.

| Système d’exploitation | Android 4.0 ou version ultérieure (niveau d’API minimal 14) |
|---|---|
| CPU | 1 GHz Coeur unique ou équivalent |
| RAM | 256 Mo |
| GPU | Unité de traitement de contenu matériel requise pour la lecture |
| Architecture | x86 via Houdini, ARM64, ARMv7 et ARMv8 |

## Exigences en matière de contenu et de manifeste {#section_72DD0E4DA9774DCCADB42887497F1386}

Vérifiez les restrictions et les exigences pour les flux et les listes de lecture (manifestes), y compris les clés de chiffrement DRM.

| Adobe Access DRM | Si le flux protégé par DRM est à débit multiple (MBR), la clé de chiffrement DRM utilisée pour le MBR doit être la même que celle utilisée dans tous les flux de débit. |
|---|---|
| Manifestations de variantes d&#39;annonces | Doit comporter les mêmes rendus de débit que les rendus du contenu principal. |

## #EXT-X-VERSION conditions requises {#section_49A33664651A46EC9ED888BA9C1C3F6D}

La version de `#EXT-X-VERSION` dans le [!DNL .m3u8] Le fichier manifeste affecte les fonctionnalités disponibles pour votre application et celles qui `EXT` Les balises sont valides.

Voici quelques informations sur la `#EXT-X-VERSION` qui spécifie la version du protocole HLS :

* La version doit correspondre aux fonctionnalités et attributs de la liste de lecture HLS ; dans le cas contraire, des erreurs de lecture peuvent se produire. Pour plus d’informations, voir [Spécification HTTP Live Streaming](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1).
* Adobe recommande d’utiliser au moins la version 2 de HLS pour la lecture dans les clients basés sur TVSDK.

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
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:2 </span> </td> 
   <td colname="2"> L’attribut IV de la variable <span class="codeph"> EXT-X-KEY </span> balise . </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Point flottant <span class="codeph"> EXTINF </span> valeurs de durée <p>The duration tags ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in version 2 were rounded to integer values. Les versions 3 et ultérieures nécessitent que les durées soient spécifiées exactement, en virgule flottante. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_5E73D41AF6DC4CEE88D6C029FFCFC350">Le <span class="codeph"> EXT-X-BYTERANGE </span> tag </li> 
     <li id="li_BF5141F516F749E5890860D487EB5287">Le <span class="codeph"> EXT-X-I-FRAME-STREAM-INF </span> tag </li> 
     <li id="li_E0D399A13812499B94107CDE62998EE9">Le <span class="codeph"> EXT-X-I-FRAMES-ONLY </span> tag </li> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">Le <span class="codeph"> EXT-X-MEDIA </span> tag </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">Le <span class="codeph"> AUDIO </span> et <span class="codeph"> VIDÉO </span> attributs de la variable <span class="codeph"> EXT-X-STREAM-INF </span> tag </li> 
     <li id="li_DB2A7847D5884F6E91FD9E78101FBCA5">Audio alternative TVSDK </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
