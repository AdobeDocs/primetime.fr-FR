---
description: Le contenu d’un AdAsset décrit une bannière connexe.
seo-description: Le contenu d’un AdAsset décrit une bannière connexe.
seo-title: Données de bannière d’accompagnement
title: Données de bannière d’accompagnement
uuid: 4a5d78e1-5abe-45a8-b50f-14f73fdcc879
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# Données de bannière d’accompagnement {#companion-banner-data}

Le contenu d’un AdAsset décrit une bannière connexe.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

Chaque `AdAsset` fournit des informations sur l&#39;affichage de la ressource.

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
   <td colname="col2"> Largeur de la bannière d’accompagnement en pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> hauteur </td> 
   <td colname="col2"> Hauteur de la bannière d’accompagnement en pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> type de ressource </td> 
   <td colname="col2">Type de ressource pour cette bannière complémentaire : 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html : Les données sont en code HTML. </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe : Les données sont une URL iframe (src). </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> URL statique </td> 
   <td colname="col2"> <p>Parfois, la bannière associée possède également une <span class="codeph"> staticURL</span> qui est une URL directe vers l'image ou vers une <span class="codeph"> .swf</span> (bannière Flash). </p> <p>Si vous ne souhaitez pas utiliser de code html ou iframe, vous pouvez utiliser une URL directe vers une image ou un fichier swf pour afficher la bannière sur la scène du Flash. Dans ce cas, vous pouvez utiliser <span class="codeph"> staticURL</span> pour afficher la bannière. </p> <p>Important :  Vous devez vérifier si l’URL statique est une chaîne valide, car cette propriété n’est pas toujours disponible. </p> </td> 
  </tr> 
 </tbody> 
</table>

