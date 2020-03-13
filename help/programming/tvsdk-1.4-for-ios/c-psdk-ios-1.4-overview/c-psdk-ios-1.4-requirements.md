---
description: TVSDK requiert des propriétés spécifiques pour le contenu multimédia, le contenu manifeste et les versions logicielles.
seo-description: TVSDK requiert des propriétés spécifiques pour le contenu multimédia, le contenu manifeste et les versions logicielles.
seo-title: Conditions requises
title: Conditions requises
uuid: 7e5fb176-4c3f-4c12-9080-3afced28627b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Conditions requises {#requirements}

TVSDK requiert des propriétés spécifiques pour le contenu multimédia, le contenu manifeste et les versions logicielles.

## Configuration système et logiciel requise {#section_61C32A0209C44230B392B113B85643EE}

Pour utiliser TVSDK, assurez-vous que votre matériel, votre système d’exploitation et vos versions d’application répondent toutes aux exigences minimales énumérées ci-dessous.

Système d’exploitation : iOS 6.0 ou version ultérieure

## Exigences en matière de contenu et de manifeste {#section_05FA02E2189742008DA09D87E66DCAB7}

Vérifiez les restrictions et les exigences pour les flux et les listes de lecture (manifestes), y compris les clés de chiffrement DRM.

| Cadres clés du segment de contenu | Chaque segment de contenu doit commencer par un cadre clé. |
|---|---|
| Numéros de séquence dans la vidéo en direct/linéaire | Doit correspondre à tout moment entre tous les rendus de débit pour le contenu principal. |

## #EXT-X-VERSION {#section_C03D3DCE1D244E26BBD2C1D7144FDFBD}

La version de `#EXT-X-VERSION` dans le [!DNL .m3u8] fichier affecte les fonctionnalités disponibles pour votre application et les `EXT` balises valides dans votre liste de lecture/manifeste.

Voici quelques informations sur la `#EXT-X-VERSION` balise, qui spécifie la version du protocole HLS :

* La version doit correspondre aux fonctionnalités et aux attributs de la liste de lecture HLS ; dans le cas contraire, des erreurs de lecture peuvent se produire.

   Pour plus d’informations, voir la spécification [](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)HTTP Live Streaming.
* Si la balise n’est pas incluse dans les listes de lecture du média ou du maître, ou si aucune version n’est spécifiée, la version 1 est utilisée par défaut. Le contenu non conforme à la version 1 ne sera pas lu.
* Adobe recommande d’utiliser au moins la version 2 pour la lecture dans les clients basés sur TVSDK.

Les clients et les serveurs doivent implémenter les versions de la manière suivante :

<table id="table_62EB98EDD9DE49EC84CB1C7D59BC40E6"> 
 <thead> 
  <tr> 
   <th colname="1" class="entry"> Utiliser au moins cette version </th> 
   <th colname="2" class="entry"> Pour utiliser ces fonctionnalités </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:2 </span> </td> 
   <td colname="2"> Attribut IV de la <span class="codeph"> balise EXT-X-KEY </span> . </td> 
  </tr> 
  <tr> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">Valeurs de <span class="codeph"> </span> durée EXTINF à virgule flottante <p>Les balises de durée ( <span class="codeph"> #EXTINF: </span>&lt;durée&gt;,&lt;titre&gt;) dans la version 2 ont été arrondies à des valeurs entières. Les versions 3 et ultérieures exigent que les durées soient exactes en virgule flottante. </p> </li> 
     <li id="li_8DF5E91F1D5D4E19894595E1FE0A5EDE"> Fonctionnalités TVSDK telles que l’insertion d’annonces publicitaires et l’ABR transparent </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="1"> <p> <span class="codeph"> EXT-X-VERSION:4 </span> </p> </td> 
   <td colname="2"> <p> 
     <ul id="ul_99E24D013E3141308B5A57446A9B8033"> 
      <li id="li_F36E65ADD2CA451C82FF18DBD5667927">La <span class="codeph"> balise EXT-X-BYTERANGE </span> </li> 
      <li id="li_8C653168A7B84D11AC233E7548A8D2EF">La <span class="codeph"> balise EXT-X-I-FRAME-STREAM-INF </span> </li> 
      <li id="li_2922B34717CB4F6189068529CDBE6D10">La <span class="codeph"> </span> balise EXT-X-I-FRAMES-ONLY </li> 
      <li id="li_D015D78E217641D7867EB509E9F9EEE2">La <span class="codeph"> balise EXT-X-MEDIA </span> </li> 
      <li id="li_CA068EA381984F5497FE67617CA8BB34">Attributs <span class="codeph"> AUDIO </span> et <span class="codeph"> VIDEO </span> de la balise <span class="codeph"> EXT-X-STREAM-INF </span> </li> 
      <li id="li_EE78CC7D194A4EB2897F9AE8E4B081B8"> Audio alternatif TVSDK </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
