---
description: Vous pouvez fournir des informations de style pour les pistes de sous-titrage à l’aide de la classe ClosedCaptionStyles. Cela définit le style de toutes les sous-titres fermés qui sont affichés par votre lecteur.
seo-description: Vous pouvez fournir des informations de style pour les pistes de sous-titrage à l’aide de la classe ClosedCaptionStyles. Cela définit le style de toutes les sous-titres fermés qui sont affichés par votre lecteur.
seo-title: Contrôler le style de sous-titrage
title: Contrôler le style de sous-titrage
uuid: 506c06d3-8fe0-46c9-9ed6-5b35d21c021c
translation-type: tm+mt
source-git-commit: b67a9dcb0abb07f4fdff4e03d9d6c0b07ff45127

---


# Contrôler le style de sous-titrage{#control-closed-caption-styling}

Vous pouvez fournir des informations de style pour les pistes de sous-titrage à l’aide de la classe ClosedCaptionStyles. Cela définit le style de toutes les sous-titres fermés qui sont affichés par votre lecteur.

Cette classe encapsule les informations de style de sous-titrage, telles que le type de police, la taille, la couleur et l’opacité de l’arrière-plan. Une classe d’assistance associée `ClosedCaptionStylesBuilder`facilite l’utilisation des paramètres de style de sous-titrage.

## Définition des styles de sous-titrage {#section_DAE84659D1964DB1B518F91B59AF29D9}

Vous pouvez mettre en forme le texte de sous-titrage à l’aide des méthodes TVSDK.

1. Attendez que MediaPlayer ait au moins l’état PRÉPARÉ (voir [Attendre un état](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-ui-configure/t-psdk-dhls-1.4-ui-state-prepared-wait-for.md)valide).
1. Pour modifier les paramètres de style, effectuez l’une des opérations suivantes :

   * Utilisez la classe `ClosedCaptionStylesBuilder` helper (fonctionne en `ClosedCaptionStyles` coulisses).
   * Utilisez la `ClosedCaptionStyles` classe directement.

>[!NOTE]
>
>La définition du style de sous-titrage est une opération asynchrone qui peut prendre jusqu’à quelques secondes pour que les modifications s’affichent à l’écran.

## Options de style de sous-titrage {#section_D28F50B98C0D48CF89C4FB6DC81C5185}

Vous pouvez fournir des informations de style pour les pistes de sous-titrage à l’aide de la `ClosedCaptionStyles` classe. Cela définit le style de toutes les sous-titres fermés qui sont affichés par votre lecteur.

```
public function TextFormat( 
   font:String = default,  
   size:String = default,  
   fontEdge:String = default,  
   fontColor:String = default,  
   backgroundColor:String = default,  
   fillColor:String = default,  
   edgeColor:String = default,  
   fontOpacity:int,  
   backgroundOpacity:int,  
   fillOpacity:int)
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
   <td colname="2"> <p>Type de police. </p> <p>Peut uniquement être définie sur une valeur définie par le <span class="codeph"> tableau ClosedCaptionStyles.FONT </span> et représente, par exemple, un espacement monochrome avec ou sans sérifs. 
     <code class="syntax actionscript">
       public&nbsp;static&nbsp;const&nbsp;FONT&nbsp;:Array&nbsp;=&nbsp;[ 
      &nbsp;AVCaptionStyle.DEFAULT, 
      &nbsp;AVCaptionStyle.MONOSPACE_WITH_SERIFS, 
      &nbsp;AVCaptionStyle.MONOSPACED_WITHOUT_SERIFS, 
      &nbsp;AVCaptionStyle.PROPORTIONAL_WITH_SERIFS, 
      &nbsp;AVCaptionStyle.PROPORTIONAL_WITHOUT_SERIFS, 
      &nbsp;AVCaptionStyle.CASUAL, 
      &nbsp;AVCaptionStyle.CURSIVE, 
      &nbsp;AVCaptionStyle.SMALL_CAPITALS 
      &nbsp;]; 
     </code> </p> <p>Conseil :  Les polices disponibles sur un périphérique peuvent varier et des substitutions sont utilisées si nécessaire. Le monoespace avec empattements est généralement utilisé comme substitut, bien que cette substitution puisse être propre au système. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Taille </td> 
   <td colname="2"> <p>La taille de la légende. </p> <p> Peut uniquement être définie sur une valeur définie par le <span class="codeph"> tableau ClosedCaptionStyles.FONT_SIZE </span> : 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MOYEN </span> - Taille standard </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> GRAND </span> - Environ 30 % plus grand que moyen </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> PETITE </span> - Environ 30 % inférieure à moyenne </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> DEFAULT </span> - Taille par défaut de la légende ; identique à medium </li> 
     </ul> </p> <p>Conseil :  Vous pouvez modifier la taille de police des légendes WebVTT en modifiant le paramètre de taille de la <span class="codeph"> fonction de définition </span> DefaultMediaPlayer.ccStyles. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Bordure de la police </td> 
   <td colname="2"> <p>Effet utilisé pour le bord de la police, par exemple relevé ou aucun. </p> <p>Peut uniquement être définie sur une valeur définie par le <span class="codeph"> tableau </span> ClosedCaptionStyles.FONT_EDGE. 
     <code class="syntax actionscript">
       public&nbsp;static&nbsp;const&nbsp;FONT_EDGE&nbsp;:Array&nbsp;=&nbsp;[ 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DEFAULT, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.NONE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.RAISED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DEPRESSED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.UNIFORM, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.LEFT_DROP_SHADOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.RIGHT_DROP_SHADOW 
      &nbsp;]; 
     </code> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Couleur de police </td> 
   <td colname="2"> <p>Couleur de la police. </p> <p>Peut uniquement être définie sur une valeur définie par le <span class="codeph"> tableau ClosedCaptionStyles.COLOR </span> . 
     <code class="syntax actionscript">
       public&nbsp;static&nbsp;const&nbsp;COLOR&nbsp;:Array&nbsp;=&nbsp;[ 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DEFAULT, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BLACK, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.GRAY, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.WHITE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_WHITE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.RED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_RED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_RED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.GREEN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_GREEN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_GREEN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BLUE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_BLUE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_BLUE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.YELLOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_YELLOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_YELLOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.MAGENTA, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_MAGENTA, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_MAGENTA, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.CYAN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_CYAN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_CYAN&nbsp;&nbsp;&nbsp;]; 
     </code> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Edge color </td> 
   <td colname="2"> <p>Couleur de l’effet de contour. </p> <p>Peut être définie sur l’une des valeurs disponibles pour la couleur de la police. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Couleur d’arrière-plan </td> 
   <td colname="2"> <p>Couleur de la cellule de l’arrière-plan. </p> <p>Peut uniquement être définie sur des valeurs disponibles pour la couleur de la police. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Couleur de remplissage </td> 
   <td colname="2"> <p>Couleur d’arrière-plan de la fenêtre dans laquelle se trouve le texte. </p> <p>Peut être définie sur l’une des valeurs disponibles pour la couleur de la police. </p> <p>Important :  Cela ne s’applique pas aux légendes WebVTT, car WebVTT n’utilise pas cette fonctionnalité. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Opacité des polices </td> 
   <td colname="2"> <p>Opacité du texte. </p> <p>Exprimé en pourcentage de 0 (entièrement transparent) à 100 (entièrement opaque). <span class="codeph"> DEFAULT_OPACITY </span> pour la police est 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Opacité du fond </td> 
   <td colname="2"> <p>Opacité de la cellule de caractère d’arrière-plan. </p> <p>Exprimé en pourcentage de 0 (entièrement transparent) à 100 (entièrement opaque). <span class="codeph"> DEFAULT_OPACITY </span> pour l'arrière-plan est 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Opacité du remplissage </td> 
   <td colname="2"> <p>Opacité de l’arrière-plan de la fenêtre de sous-titrage. </p> <p>Exprimé en pourcentage de 0 (entièrement transparent) à 100 (entièrement opaque). <span class="codeph"> DEFAULT_OPACITY </span> pour le remplissage est égal à 0. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Exemples : Formatage des légendes {#section_63E33840B7A14D26990046E2ACF2ECA1}

Vous pouvez spécifier la mise en forme des sous-titres.

## Exemple 1 : Spécifier explicitement les valeurs de format {#section_BD7B48F3B66D4E9290E1CB2F464E08E4}

```
private function onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
    var formatBuilder:TextFormatBuilder = new TextFormatBuilder(); 
    formatBuilder.font = Font.DEFAULT,  
    formatBuilder.fontSize = FontSize.DEFAULT,  
    formatBuilder.fontEdge = FontEdge.DEFAULT,  
    formatBuilder.fontColor = Color.DEFAULT,  
    formatBuilder.backgroundColor = Color.DEFAULT,  
    formatBuilder.fillColor = Color.DEFAULT,  
    formatBuilder.edgeColor = Color.DEFAULT,  
    formatBuilder.fontOpacity = .DEFAULT_OPACITY,  
    formatBuilder.backgroundOpacity = Font.DEFAULT_OPACITY,  
    formatBuilder.fillOpacity = TextFormat.DEFAULT_OPACITY 
    mediaPlayer.set CCStyle(formatBuilder.toTextFormat()); 
} 
```

## Exemple 2 : Spécification des valeurs de format dans les paramètres {#section_147036D7C31C4010A5A7DF49997014A9}

```
/** 
* Constructor using parameters to initialize a TextFormat. 
* 
* @param font 
* The desired font. 
* @param fontSize 
* The desired text size. 
* @param fontEdge 
* The desired font edge. 
* @param fontColor 
* The desired font color. 
* @param backgroundColor 
* The desired background color. 
* @param fillColor 
* The desired fill color. 
* @param edgeColor 
* The desired color to draw the text edges. 
* @param fontOpacity 
* The desired font opacity. 
* @param backgroundOpacity 
* The desired background opacity. 
* @param fillOpacity 
* The desired fill opacity. 
*/ 
public function TextFormatBuilder(font:Font, fontSize:FontSize, fontEdge:FontEdge,  
                                  fontColor:Color, backgroundColor:Color,  
                                  fillColor:Color, edgeColor:Color, fontOpacity:int, 
                                  backgroundOpacity:int, fillOpacity:int); 
/** 
* Creates a TextFormat with the parameters supplied to this builder. 
*/ 
public function toTextFormat():TextFormat; 
... 
```
