---
description: Vous pouvez spécifier plusieurs options de style de légende. Ces options remplacent les options de style des légendes d’origine.
title: Options de style de sous-titres codés
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Options de style de sous-titres codés{#closed-caption-styling-options}

Vous pouvez spécifier plusieurs options de style de légende. Ces options remplacent les options de style des légendes d’origine.

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
>Dans les options qui définissent des valeurs par défaut (par exemple, `DEFAULT`), cette valeur fait référence au paramètre défini lors de la spécification initiale de la légende.

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
   <td colname="2"> <p>Type de police. </p> <p>Peut uniquement être définie sur une valeur définie par la variable <span class="codeph"> TextFormat.Font </span> énumération et représente, par exemple, un espacement fixe avec ou sans sérifs. </p> <p>Conseil : Les polices disponibles sur un appareil peuvent varier et des substitutions sont utilisées si nécessaire. Le monoespace avec des sérifs est généralement utilisé comme substitut, bien que cette substitution puisse être spécifique au système. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Taille </td> 
   <td colname="2"> <p>La taille de la légende. </p> <p> Peut uniquement être définie sur une valeur définie par la variable <span class="codeph"> TextFormat.Size </span> enumeration : 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM </span> - Taille standard </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> GRAND </span> - Environ 30 % plus grand que moyen </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> PETIT </span> - Environ 30 % plus petit que moyen </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> PAR DÉFAUT </span> - Taille par défaut de la légende, identique à moyenne </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Police couleur </td> 
   <td colname="2"> <p>Couleur de police. </p> <p>Peut uniquement être définie sur une valeur définie par la variable <span class="codeph"> TextFormat.Color </span> énumération. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Couleur d’arrière-plan </td> 
   <td colname="2"> <p>Couleur de la cellule de caractère d’arrière-plan. </p> <p>Peut uniquement être défini sur les valeurs disponibles pour la couleur de police. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Opacité des polices </td> 
   <td colname="2"> <p>Opacité du texte. </p> <p>Exprimé sous la forme d’un pourcentage compris entre 0 (totalement transparent) et 100 (entièrement opaque). <span class="codeph"> DEFAULT_OPACITY </span> pour la police est 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Inset inférieur </td> 
   <td colname="2"> <p>Distance verticale depuis le bas de la fenêtre des légendes à éviter. </p> <p>Exprimé sous la forme d’un pourcentage de la hauteur de la fenêtre de légende (par exemple, "20 %") ou d’un nombre de pixels (par exemple, "20"). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Zone sécurisée </td> 
   <td colname="2"> <p>Zone autour du bord de l’écran entre 0 % et 25 % où les sous-titres n’apparaissent pas. </p> <p>Par défaut, la zone sécurisée pour 608/708 est de 12 % et celle pour WebVTT de 0 %. Ce paramètre permet à votre application de remplacer cette valeur par défaut. Si deux valeurs sont fournies, par exemple, la chaîne "10 %,20 %", la première valeur est la zone horizontale sécurisée et la seconde est la zone verticale sécurisée. Si une valeur est fournie, par exemple, la chaîne "15 %", les axes vertical et horizontal utilisent tous deux la zone de sécurité spécifiée. </p> </td> 
  </tr> 
 </tbody> 
</table>
