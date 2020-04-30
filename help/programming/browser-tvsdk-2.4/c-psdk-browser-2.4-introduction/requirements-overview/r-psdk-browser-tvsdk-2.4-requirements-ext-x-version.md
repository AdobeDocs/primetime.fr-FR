---
description: 'La version de #EXT-X-VERSION dans le fichier .m3u8 affecte les fonctionnalités disponibles pour votre application et les balises EXT valides dans votre liste de lecture/manifeste.'
seo-description: 'La version de #EXT-X-VERSION dans le fichier .m3u8 affecte les fonctionnalités disponibles pour votre application et les balises EXT valides dans votre liste de lecture/manifeste.'
seo-title: '#EXT-X-VERSION requirements'
title: '#EXT-X-VERSION requirements'
uuid: 8d22930f-4faf-4a40-b1f0-507886cd8938
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# #EXT-X-VERSION requirements{#ext-x-version-requirements}

La version de #EXT-X-VERSION dans le fichier .m3u8 affecte les fonctionnalités disponibles pour votre application et les balises EXT valides dans votre liste de lecture/manifeste.

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

Voici quelques informations sur la `#EXT-X-VERSION` balise, qui spécifie la version du protocole HLS :

* La version doit correspondre aux fonctionnalités et aux attributs de la liste de lecture HLS ; sinon, des erreurs de lecture peuvent se produire. Pour plus d’informations, voir Spécification [de diffusion en flux continu en direct](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)HTTP.
* Adobe recommande d’utiliser au moins la version 2 pour la lecture dans les clients basés sur le navigateur TVSDK.

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
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Valeurs de <span class="codeph"> </span> durée EXTINF à virgule flottante <p>Les balises de durée ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) dans la version 2 ont été arrondis à des valeurs entières. Les versions 3 et ultérieures exigent que les durées soient exactes en virgule flottante. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">La balise <span class="codeph"> EXT-X-MEDIA </span> </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">Attributs <span class="codeph"> AUDIO </span> et <span class="codeph"> VIDEO </span> de la balise <span class="codeph"> </span> EXT-X-STREAM-INF </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

