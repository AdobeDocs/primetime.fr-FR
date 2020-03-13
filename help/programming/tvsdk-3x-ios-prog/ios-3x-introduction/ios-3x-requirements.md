---
description: TVSDK a des exigences spécifiques pour le contenu multimédia, le contenu manifeste, la gestion des droits numériques et les versions logicielles.
seo-description: TVSDK a des exigences spécifiques pour le contenu multimédia, le contenu manifeste, la gestion des droits numériques et les versions logicielles.
seo-title: Conditions requises
title: Conditions requises
uuid: 06e61b9f-cda2-4813-8da4-fb3e0d88ad35
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Conditions requises {#requirements}

TVSDK requiert des propriétés spécifiques pour le contenu multimédia, le contenu manifeste, la gestion des droits numériques et les versions logicielles.

## Configuration système et logiciel requise {#section_96E5B079900246E78682AE44D3F23068}

Pour utiliser TVSDK, assurez-vous que votre matériel, votre système d’exploitation et vos versions d’application répondent toutes aux exigences minimales énumérées ci-dessous.

| Système d’exploitation | iOS 7.0 ou version ultérieure |
|---|---|
| Xcode | Xcode 10 pour iOS 12 et Xcode 9 pour iOS 11 |

## Exigences en matière de contenu et de manifeste {#section_72DD0E4DA9774DCCADB42887497F1386}

Vérifiez les restrictions et les exigences pour les flux et les listes de lecture (manifestes), y compris les clés de chiffrement DRM.

| Cadres clés du segment de contenu | Chaque segment de contenu doit commencer par un cadre clé. |
|---|---|
| Numéros de séquence dans la vidéo en direct/linéaire | Doit correspondre à tout moment entre tous les rendus de débit pour le contenu principal. |

## EXT-X-VERSION {#section_C03D3DCE1D244E26BBD2C1D7144FDFBD}

La version de `#EXT-X-VERSION` dans le fichier [!DNL .m3u8] manifeste affecte les fonctionnalités disponibles pour votre application et les `EXT` balises valides.

Voici quelques informations sur la `#EXT-X-VERSION` balise, qui spécifie la version du protocole HLS :

* La version doit correspondre aux fonctionnalités et aux attributs de la liste de lecture HLS ; dans le cas contraire, des erreurs de lecture peuvent se produire. Pour plus d’informations, voir la spécification [](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)HTTP Live Streaming.
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
   <td colname="2"> Attribut IV de la <span class="codeph"> balise EXT-X-KEY </span> . </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Valeurs de <span class="codeph"> </span> durée EXTINF à virgule flottante <p>Les balises de durée ( <span class="codeph"> #EXTINF: </span>&lt;durée&gt;,&lt;titre&gt;) dans la version 2 ont été arrondies à des valeurs entières. Les versions 3 et ultérieures exigent que les durées soient spécifiées exactement, en virgule flottante. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_5E73D41AF6DC4CEE88D6C029FFCFC350">La <span class="codeph"> balise EXT-X-BYTERANGE </span> </li> 
     <li id="li_BF5141F516F749E5890860D487EB5287">La <span class="codeph"> balise EXT-X-I-FRAME-STREAM-INF </span> </li> 
     <li id="li_E0D399A13812499B94107CDE62998EE9">La <span class="codeph"> </span> balise EXT-X-I-FRAMES-ONLY </li> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">La <span class="codeph"> balise EXT-X-MEDIA </span> </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">Attributs <span class="codeph"> AUDIO </span> et <span class="codeph"> VIDEO </span> de la balise <span class="codeph"> EXT-X-STREAM-INF </span> </li> 
     <li id="li_DB2A7847D5884F6E91FD9E78101FBCA5">Audio alternatif TVSDK </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>