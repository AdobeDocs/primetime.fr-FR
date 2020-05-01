---
description: Vous pouvez spécifier plusieurs options de style de légende et ces options remplacent les options de style dans les légendes d’origine.
seo-description: Vous pouvez spécifier plusieurs options de style de légende et ces options remplacent les options de style dans les légendes d’origine.
seo-title: Options de style de sous-titrage
title: Options de style de sous-titrage
uuid: 0e2fd9f3-e569-4b5d-9b78-86f8ee6230ee
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Options de style de sous-titrage{#closed-caption-styling-options}

Vous pouvez spécifier plusieurs options de style de légende et ces options remplacent les options de style dans les légendes d’origine.

```js
new TextFormat( 
   font,  
   fontColor,  
   edgeColor,  
   fontEdge,  
   backgroundColor,  
   fillColor,  
   size,  
   fontOpacity,  
   backgroundOpacity,  
   fillOpacity, 
   bottomInset, 
   safeArea) 
```

>[!TIP]
>
>Dans les options qui définissent les valeurs par défaut (par exemple `DEFAULT`), cette valeur fait référence à ce que le paramètre était lorsque la légende a été initialement spécifiée.

<table frame="all" colsep="1" rowsep="1" id="table_87205DEFEE384AF4AF83952B15E18A42"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Format </th> 
   <th colname="2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> Police </td> 
   <td colname="2"> <p>Type de police. </p> <p>Peut uniquement être définie sur une valeur définie par la <span class="codeph"> énumération </span> TextFormat.Font et qui représente, par exemple, un espacement monochrome avec ou sans sérifs. </p> <p>Conseil :  Les polices disponibles sur un périphérique peuvent varier et des substitutions sont utilisées si nécessaire. Le monoespace avec empattements est généralement utilisé comme substitut, bien que cette substitution puisse être propre au système. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Taille </td> 
   <td colname="2"> <p>La taille de la légende. </p> <p> Peut uniquement être définie sur une valeur définie par la <span class="codeph"> énumération TextFormat.Size </span> : 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MOYEN </span> - Taille standard </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> GRAND </span> - Environ 30 % plus grand que moyen </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> PETITE </span> - Environ 30 % inférieure à moyenne </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> DEFAULT </span> - Taille par défaut de la légende ; identique à medium </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Couleur de police </td> 
   <td colname="2"> <p>Couleur de la police. </p> <p>Peut uniquement être définie sur une valeur définie par la <span class="codeph"> énumération TextFormat.Color </span> . </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Couleur d’arrière-plan </td> 
   <td colname="2"> <p>Couleur de la cellule de l’arrière-plan. </p> <p>Peut uniquement être définie sur des valeurs disponibles pour la couleur de la police. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Opacité des polices </td> 
   <td colname="2"> <p>Opacité du texte. </p> <p>Exprimé en pourcentage de 0 (entièrement transparent) à 100 (entièrement opaque). <span class="codeph"> DEFAULT_OPACITY </span> pour la police est 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Entrée inférieure </td> 
   <td colname="2"> <p>Distance verticale par rapport au bas de la fenêtre de sous-titrage pour les légendes à éviter. </p> <p>Exprimé sous forme de pourcentage de la hauteur de la fenêtre de légende (par exemple, "20 %") ou d’un nombre de pixels (par exemple, "20"). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Zone sécurisée </td> 
   <td colname="2"> <p>Zone située autour du bord de l’écran, entre 0 % et 25 %, dans laquelle les légendes n’apparaissent pas. </p> <p>Par défaut, la zone de sécurité pour 608/708 est de 12 % et la zone de sécurité pour WebVTT est de 0 %. Ce paramètre permet à votre application de remplacer cette valeur par défaut. Si deux valeurs sont fournies, par exemple, la chaîne "10 %,20 %", la première valeur est la zone horizontale sécurisée et la seconde, la zone verticale sécurisée. Si une valeur est fournie, par exemple, la chaîne "15%", les axes vertical et horizontal utilisent tous deux la zone de sécurité spécifiée. </p> </td> 
  </tr> 
 </tbody> 
</table>

