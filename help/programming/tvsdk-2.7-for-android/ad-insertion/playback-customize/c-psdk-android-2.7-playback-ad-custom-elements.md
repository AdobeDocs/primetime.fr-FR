---
description: TVSDK fournit des classes et des méthodes que vous pouvez utiliser pour personnaliser le comportement de lecture du contenu qui contient de la publicité.
seo-description: TVSDK fournit des classes et des méthodes que vous pouvez utiliser pour personnaliser le comportement de lecture du contenu qui contient de la publicité.
seo-title: Eléments d’API pour la lecture de publicités
title: Eléments d’API pour la lecture de publicités
uuid: 5e21e709-8446-4fed-8711-aa4f629f1147
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Eléments d’API pour la lecture de publicités {#api-elements-for-ad-playback}

TVSDK fournit des classes et des méthodes que vous pouvez utiliser pour personnaliser le comportement de lecture du contenu qui contient de la publicité.

Les éléments d’API suivants sont utiles pour personnaliser la lecture :

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elément API </th> 
   <th colname="col2" class="entry"> Contenu prenant en charge la publicité </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdvertisingMetadata </span> </td> 
   <td colname="col2">Déterminer si une coupure publicitaire doit être marquée comme ayant été regardée par un lecteur et, dans l’affirmative, quand la marquer. Définissez et obtenez la stratégie de contrôle à l’aide de <span class="codeph"> setAdBreakAsWatched</span> et <span class="codeph"> getAdBreakAsWatched</span>. </td> 
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
   <td colname="col2"> Interface qui permet la personnalisation du comportement des annonces TVSDK. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> DefaultAdPolicySelector </span> </td> 
   <td colname="col2"> Classe qui implémente le comportement par défaut de TVSDK. Votre application peut remplacer cette classe pour personnaliser les comportements par défaut sans mettre en oeuvre l'interface complète. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="apiname"> MediaPlayer</span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"><span class="codeph"> getLocalTime</span> <p>Il s’agit de l’heure locale de lecture, à l’exclusion des pauses publicitaires importées. </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"><span class="codeph"> searchToLocal</span>. <p>Ici, la recherche se produit par rapport à une heure locale du flux. </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"><span class="codeph"> getTimeline.convertToLocalTime</span>. <p>La position virtuelle sur la chronologie est convertie en position locale. </p> </li> 
    </ul> <p>Important :  <span class="codeph"> getLocalTime</span> dans <span class="codeph"> MediaPlayer</span> renvoie l’heure actuelle par rapport au contenu d’origine, sans publicité épissée de manière dynamique. <span class="codeph"> getLocalTime</span> dans <span class="codeph"> AdBreak</span> renvoie l’heure de début de la coupure par rapport au contenu d’origine. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="apiname"> AdBreak</span> </td> 
   <td colname="col2"><span class="codeph"> isWatched</span> , propriété. Indique si le lecteur a regardé la publicité. </td> 
  </tr> 
 </tbody> 
</table>

