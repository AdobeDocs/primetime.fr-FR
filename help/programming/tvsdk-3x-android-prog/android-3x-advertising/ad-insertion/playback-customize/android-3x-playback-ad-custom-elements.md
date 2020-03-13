---
description: TVSDK fournit des classes et des méthodes que vous pouvez utiliser pour personnaliser le comportement de lecture du contenu qui contient de la publicité.
seo-description: TVSDK fournit des classes et des méthodes que vous pouvez utiliser pour personnaliser le comportement de lecture du contenu qui contient de la publicité.
seo-title: Eléments API pour la lecture de publicités
title: Eléments API pour la lecture de publicités
uuid: 56844663-d635-4b04-b61b-cb8f33ef5732
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Eléments API pour la lecture de publicités {#api-elements-for-ad-playback}

TVSDK fournit des classes et des méthodes que vous pouvez utiliser pour personnaliser le comportement de lecture du contenu qui contient de la publicité.

Les éléments d’API suivants sont utiles pour personnaliser la lecture :

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> <b>Elément API </b></th> 
   <th colname="col2" class="entry"> <b>Contenu prenant en charge la publicité</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdvertisingMetadata </span> </td> 
   <td colname="col2">Indiquez si une coupure publicitaire doit être marquée comme ayant été regardée par un lecteur et, dans l’affirmative, quand la marquer. Définissez et obtenez la stratégie de contrôle à l’aide de <span class="codeph"> setAdBreakAsWatched</span> et <span class="codeph"> getAdBreakAsWatched</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdBreakPolicy</span> </td> 
   <td colname="col2"> Énumère les stratégies de lecture possibles pour les pauses publicitaires. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdPolicy</span> </td> 
   <td colname="col2"> Énumère les stratégies de lecture possibles pour les publicités. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdPolicySelector </span> </td> 
   <td colname="col2"> Interface qui permet la personnalisation du comportement de l’annonce TVSDK. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> DefaultAdPolicySelector </span> </td> 
   <td colname="col2"> Classe qui implémente le comportement par défaut de TVSDK. Votre application peut remplacer cette classe pour personnaliser les comportements par défaut sans mettre en oeuvre l’interface complète. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="apiname"> MediaPlayer</span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"><span class="codeph"> getLocalTime</span> <p>Il s’agit de l’heure locale de la lecture, à l’exclusion des coupures publicitaires importées. </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"><span class="codeph"> searchToLocal</span>. <p>Ici, la recherche se produit par rapport à une heure locale dans le flux. </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"><span class="codeph"> getTimeline.convertToLocalTime</span>. <p>La position virtuelle sur le plan de montage chronologique est convertie en position locale. </p> </li> 
    </ul> <p>Important :  <span class="codeph"> getLocalTime</span> dans <span class="codeph"> MediaPlayer</span> renvoie l’heure actuelle par rapport au contenu d’origine, sans publicité avec épissée dynamiquement. <span class="codeph"> getLocalTime</span> dans <span class="codeph"> AdBreak</span> renvoie l’heure de  du saut par rapport au contenu d’origine. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdBreak</span> </td> 
   <td colname="col2"><span class="codeph"> isWatched</span> , propriété. Indique si le lecteur a regardé la publicité. </td> 
  </tr> 
 </tbody> 
</table>