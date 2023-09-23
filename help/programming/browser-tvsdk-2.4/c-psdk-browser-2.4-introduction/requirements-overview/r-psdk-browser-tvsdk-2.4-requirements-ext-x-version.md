---
description: La version de EXT-X-VERSION dans le fichier .m3u8 affecte les fonctionnalités disponibles pour votre application et les balises EXT valides dans votre playlist/manifeste.
title: Exigences pour EXT-X-VERSION
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# Exigences pour EXT-X-VERSION{#ext-x-version-requirements}

La version de `#EXT-X-VERSION` dans le fichier .m3u8 affecte les fonctionnalités disponibles pour votre application et les balises EXT valides dans votre playlist/manifeste.

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

Voici quelques informations sur la balise, qui spécifie la `#EXT-X-VERSION` version du protocole HLS :

* La version doit correspondre aux caractéristiques et attributs de la liste de lecture HLS ; Sinon, des erreurs de lecture risquent de se produire. Pour plus d’informations, consultez [Spécification HTTP Live Streaming](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1).
* Adobe recommande d’utiliser au moins la version 2 pour la lecture dans les clients TVSDK du navigateur.

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
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Valeurs de durée EXTINF </span> en virgule <span class="codeph"> flottante <p>Les balises de durée ( <span class="codeph"> #EXTINF : </span>&lt;duration&gt;,&lt;title&gt;) dans la version 2 étaient arrondies à des valeurs entières. &lt;/title&gt;&lt;/duration&gt; Les versions 3 et ultérieures exigent que les durées soient exactes en virgule flottante. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">La <span class="codeph"> balise EXT-X-MEDIA </span> </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">Attributs <span class="codeph"> AUDIO </span> et <span class="codeph"> VIDEO </span> de la <span class="codeph"> balise EXT-X-STREAM-INF </span> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
