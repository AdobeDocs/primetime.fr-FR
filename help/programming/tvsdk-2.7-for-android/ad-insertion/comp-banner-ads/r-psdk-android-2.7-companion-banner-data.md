---
description: Le contenu d’une AdAsset décrit une bannière compagnon.
title: Companion banner data
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# Companion banner data {#companion-banner-data}

Le contenu d’une AdAsset décrit une bannière compagnon.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

Chaque `AdAsset` fournit des informations sur l’affichage de la ressource.

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Informations disponibles </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> width </td> 
   <td colname="col2"> Largeur de la bannière compagnon en pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> height </td> 
   <td colname="col2"> Hauteur de la bannière compagnon en pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> type de ressource </td> 
   <td colname="col2">Type de ressource pour cette bannière compagnon : 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html : les données se trouvent dans le code du HTML. </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe : les données sont une URL iframe (src). </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> URL statique </td> 
   <td colname="col2"> <p>Parfois, la bannière compagnon comporte également une <span class="codeph"> staticURL</span> qui est une URL directe vers l’image ou vers une <span class="codeph"> .swf</span> (bannière Flash). </p> <p>Si vous ne souhaitez pas utiliser de code html ou iframe, vous pouvez utiliser une URL directe vers une image ou un fichier swf pour afficher la bannière dans l’étape du Flash. Dans ce cas, vous pouvez utiliser le <span class="codeph"> staticURL</span> pour afficher la bannière. </p> <p>Important : Vous devez vérifier si l’URL statique est une chaîne valide, car cette propriété peut ne pas toujours être disponible. </p> </td> 
  </tr> 
 </tbody> 
</table>
