---
description: Le contenu d’un AdBannerAsset décrit une bannière connexe.
seo-description: Le contenu d’un AdBannerAsset décrit une bannière connexe.
seo-title: Données de bannière d’accompagnement
title: Données de bannière d’accompagnement
uuid: b2c709da-9d19-49d1-8116-9c947371b77c
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---


# Données de bannière d’accompagnement{#companion-banner-data}

Le contenu d’un AdBannerAsset décrit une bannière connexe.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

Le `AdobePSDK.PSDKEventType.AD_STARTED` événement renvoie une `Ad` instance contenant une `companionAssets` propriété ( `Array<AdBannerAsset>`).
Chacune `AdBannerAsset` fournit des informations sur l’affichage de la ressource.

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
     <li id="li_48E74AC5F00640EC8A4DE2CB31E106EC">static: Les données sont une URL d’image statique (src). </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1">
    <pre>
      données de bannière
    </pre> </td> 
   <td colname="col2"> Données du type spécifié par <span class="codeph"> resourceType</span> pour cette bannière complémentaire. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> URL statique </td> 
   <td colname="col2"> <p>Parfois, la bannière associée peut également avoir une URL statique qui est une URL directe vers l’image. </p> <p>Si vous ne souhaitez pas utiliser de code html ou iframe, vous pouvez utiliser une URL directe vers une image. Dans ce cas, vous pouvez utiliser staticURL pour afficher la bannière. </p> <p>Important :  Vous devez vérifier si l’URL statique est une chaîne valide, car cette propriété n’est pas toujours disponible. </p> </td> 
  </tr> 
 </tbody> 
</table>

