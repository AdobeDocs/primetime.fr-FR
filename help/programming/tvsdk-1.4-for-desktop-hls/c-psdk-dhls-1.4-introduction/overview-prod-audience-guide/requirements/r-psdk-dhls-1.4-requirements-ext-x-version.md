---
description: 'La version de #EXT-X-VERSION dans le fichier .m3u8 affecte les fonctionnalités disponibles pour votre application et les balises EXT valides dans votre liste de lecture/manifeste.'
seo-description: 'La version de #EXT-X-VERSION dans le fichier .m3u8 affecte les fonctionnalités disponibles pour votre application et les balises EXT valides dans votre liste de lecture/manifeste.'
seo-title: '#EXT-X-VERSION requirements'
title: '#EXT-X-VERSION requirements'
uuid: c862df4a-88ba-4497-8b7c-b83fcb34b8bb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# #EXT-X-VERSION requirements{#ext-x-version-requirements}

La version de #EXT-X-VERSION dans le fichier .m3u8 affecte les fonctionnalités disponibles pour votre application et les balises EXT valides dans votre liste de lecture/manifeste.

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

Voici quelques informations sur la `#EXT-X-VERSION` balise, qui spécifie la version du protocole HLS :

* La version doit correspondre aux fonctionnalités et aux attributs de la liste de lecture HLS ; sinon, des erreurs de lecture peuvent se produire.

   Pour plus d’informations, voir Spécification [de diffusion en flux continu en direct](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)HTTP.
* La version doit correspondre aux fonctionnalités et aux attributs de la liste de lecture HLS ; sinon, des erreurs de lecture peuvent se produire.

   Pour plus d’informations, voir Spécification [de diffusion en flux continu en direct](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)HTTP.
* Adobe recommande d’utiliser au moins la version 2 pour la lecture sur des clients basés sur le contenu.

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
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Valeurs de <span class="codeph"> </span> durée EXTINF à virgule flottante <p>Les balises de durée ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) dans la version 2 ont été arrondis à des valeurs entières. Les versions 3 et ultérieures exigent que les durées soient exactes en virgule flottante. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <p> <span class="codeph"> EXT-X-VERSION:4 </span> </p> </td> 
   <td colname="2"> <p> 
     <ul id="ul_83D61E909D0C413FBDAB7A4A0BE1F03C"> 
      <li id="li_5071F2BE2DB74BBFB1F23B3B30C5CFD6">La <span class="codeph"> balise EXT-X-BYTERANGE </span> </li> 
      <li id="li_A093F448567D475AB44656D4600BCBD6">La <span class="codeph"> balise EXT-X-I-FRAME-STREAM-INF </span> </li> 
      <li id="li_1084AE3B10FD4EB387D25EEDDFBBC8CD">La <span class="codeph"> balise </span> EXT-X-I-FRAMES-ONLY </li> 
      <li id="li_4FEFA36E300C403DBB77BB4DA46DB4EB">La balise <span class="codeph"> EXT-X-MEDIA </span> </li> 
      <li id="li_E53D81AED45C47AEA346FA3A1B191E5C">Attributs <span class="codeph"> AUDIO </span> et <span class="codeph"> VIDEO </span> de la balise <span class="codeph"> </span> EXT-X-STREAM-INF </li> 
      <li id="li_2E99A4971B8046F3845CF3D4D363CCCF">Audio alternatif TVSDK </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

