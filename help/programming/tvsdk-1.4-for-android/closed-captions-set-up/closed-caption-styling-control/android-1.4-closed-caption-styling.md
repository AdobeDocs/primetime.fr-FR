---
description: Vous pouvez fournir des informations de style pour les pistes de sous-titrage à l’aide de la classe TextFormat. Cela définit le style de toutes les sous-titres fermés qui sont affichés par votre lecteur.
seo-description: Vous pouvez fournir des informations de style pour les pistes de sous-titrage à l’aide de la classe TextFormat. Cela définit le style de toutes les sous-titres fermés qui sont affichés par votre lecteur.
seo-title: Contrôler le style de sous-titrage
title: Contrôler le style de sous-titrage
uuid: 331b0833-3e8a-482e-a3df-5e92b69d0a94
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Contrôler le style de sous-titrage {#control-closed-caption-styling-overview}

Vous pouvez fournir des informations de style pour les pistes de sous-titrage à l’aide de la classe TextFormat. Cela définit le style de toutes les sous-titres fermés qui sont affichés par votre lecteur.

Cette classe encapsule les informations de style de sous-titrage, telles que le type de police, la taille, la couleur et l’opacité de l’arrière-plan. Une classe d’assistance associée `TextFormatBuilder`facilite l’utilisation des paramètres de style de sous-titrage.

## Définition des styles de sous-titrage {#set-closed-caption-styles}

Vous pouvez mettre en forme le texte de sous-titrage à l’aide des méthodes TVSDK.

1. Attendez que le lecteur multimédia soit au moins à l’état PRÉPARÉ.
1. Créez une `TextFormatBuilder` instance.

   Vous pouvez fournir tous les paramètres de style de sous-titrage ou les définir ultérieurement.

   TVSDK encapsule les informations de style de sous-titrage codé dans l’ `TextFormat` interface. La `TextFormatBuilder` classe crée des objets qui implémentent cette interface.

   ```java
   public TextFormatBuilder( 
      Font font, 
      Size size, 
      FontEdge fontEdge, 
      Color fontColor, 
      Color backgroundColor, 
      Color fillColor, 
      Color edgeColor, 
      int fontOpacity, 
      int backgroundOpacity, 
      int fillOpacity)
   ```

1. Pour obtenir une référence à un objet qui implémente l&#39; `TextFormat` interface, appelez la méthode `TextFormatBuilder.toTextFormat` publique.

   Cette opération renvoie un `TextFormat` objet qui peut être appliqué au lecteur de médias.

   ```java
   public TextFormat toTextFormat()
   ```

1. Vous pouvez également obtenir les paramètres actuels de style de sous-titrage en procédant de l’une des manières suivantes :

   * Obtenez tous les paramètres de style avec `MediaPlayer.getCCStyle`.

      La valeur renvoyée est une instance de l’ `TextFormat` interface.

      ```js
      /** 
      * @return the current closed captioning style.  
      * If no style was previously set, it returns a TextFormat object 
      * with default values for each attribute. 
      * @throws IllegalStateException if media player was already released. 
      */ 
      public TextFormat getCCStyle() throws IllegalStateException;
      ```

   * Récupérez les paramètres un par un grâce aux méthodes d&#39;obtention de l&#39; `TextFormat` interface.

      ```js
      public Color getFontColor(); 
      public Color getBackgroundColor(); 
      public Color getFillColor(); // retrieve the font fill color 
      public Color getEdgeColor(); // retrieve the font edge color 
      public Size getSize(); // retrieve the font size 
      public FontEdge getFontEdge(); // retrieve the font edge type 
      public Font getFont(); // retrieve the font type 
      public int getFontOpacity(); 
      public int getBackgroundOpacity();
      ```

1. Pour modifier les paramètres de style, effectuez l’une des opérations suivantes :

   >[!NOTE]
   >
   >Vous ne pouvez pas modifier la taille des légendes WebVTT.

   * Utilisez la méthode setter `MediaPlayer.setCCStyle`, en transmettant une instance de l’ `TextFormat` interface :

      ```js
      /** 
      * Sets the closed captioning style. Used to control the closed captioning font, 
      * size, color, edge and opacity.  
      * 
      * This method is safe to use even if the current media stream doesn't have closed 
      * captions. 
      * 
      * @param textFormat 
      * @throws IllegalStateException 
      */ 
      public void setCCStyle(TextFormat textFormat) throws IllegalStateException;
      ```

   * Utilisez la `TextFormatBuilder` classe, qui définit des méthodes de définition individuelles.

      L&#39; `TextFormat` interface définit un objet immuable, de sorte qu&#39;il n&#39;y a que les méthodes get et pas de paramètres. Vous pouvez définir les paramètres de style de sous-titrage uniquement avec la `TextFormatBuilder` classe :

      ```js
      // set font type 
      public void setFont(Font font)  
      public void setBackgroundColor(Color backgroundColor) 
      public void setFillColor(Color fillColor) 
      // set the font-edge color 
      public void setEdgeColor(Color edgeColor)  
      // set the font size 
      public void setSize(Size size)  
      // set the font edge type 
      public void setFontEdge(FontEdge fontEdge)  
      public void setFontOpacity(int fontOpacity) 
      public void setBackgroundOpacity(int backgroundOpacity) 
      // set the font-fill opacity level 
      public void setFillOpacity(int fillOpacity)  
      public void setFontColor(Color fontColor)
      ```

La définition du style de sous-titrage est une opération asynchrone qui peut prendre jusqu’à quelques secondes pour que les modifications s’affichent à l’écran.

## Options de style de sous-titrage {#closed-caption-styling-options}

Vous pouvez spécifier plusieurs options de style de légende et ces options remplacent les options de style dans les légendes d’origine.

```
public TextFormatBuilder(
 Font font,
 Size size,
 FontEdge fontEdge,
 Color fontColor,
 Color backgroundColor,
 Color fillColor,
 Color edgeColor,
 int fontOpacity,
 int backgroundOpacity,
 int fillOpacity,
 String bottomInset)
```

[!TIP]
Dans les options qui définissent les valeurs par défaut (par exemple, DEFAULT), cette valeur fait référence à ce que le paramètre était lorsque la légende a été initialement spécifiée.

<table frame="all" colsep="1" rowsep="1" id="table_87205DEFEE384AF4AF83952B15E18A42"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b> Format </b></th> 
   <th colname="2" class="entry"> <b>Description</b> </th> 
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
   <td colname="1"> Bordure de la police </td> 
   <td colname="2"> <p>Effet utilisé pour le bord de la police, par exemple relevé ou aucun. </p> <p>Peut uniquement être définie sur une valeur définie par la <span class="codeph"> énumération TextFormat.FontEdge </span> . </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Couleur de police </td> 
   <td colname="2"> <p>Couleur de la police. </p> <p>Peut uniquement être définie sur une valeur définie par la <span class="codeph"> énumération TextFormat.Color </span> . </p> </td> 
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
   <td colname="2"> <p>Couleur d’arrière-plan de la fenêtre dans laquelle se trouve le texte. </p> <p>Peut être définie sur l’une des valeurs disponibles pour la couleur de la police. </p> </td> 
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

## Exemples de formatage des légendes {#examples-caption-formatting}

Vous pouvez spécifier la mise en forme des sous-titres.

**Exemple 1 : Spécifier explicitement les valeurs de format**

```java
private final MediaPlayer.PlaybackEventListener  
  _playbackEventListener = new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() { 
        // Set CC style. 
        TextFormat tf = new TextFormatBuilder(TextFormat.Font.DEFAULT, 
        TextFormat.Size.DEFAULT, 
        TextFormat.FontEdge.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.DEFAULT_OPACITY, 
        TextFormat.DEFAULT_OPACITY, 
        TextFormat.DEFAULT_OPACITY).toTextFormat(); 
        mediaPlayer.setCCStyle(tf); 
        ... 
    } 
} 
```

**Exemple 2 : Spécification des valeurs de format dans les paramètres**

```java
/** 
* Constructor using parameters to initialize a TextFormat. 
* 
* @param font 
* The desired font. 
* @param size 
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
public TextFormatBuilder( 
    Font font, Size size, FontEdge fontEdge, 
    Color fontColor, Color backgroundColor,  
    Color fillColor, Color edgeColor, 
    int fontOpacity, int backgroundOpacity, 
    int fillOpacity); 
 
/** 
* Creates a TextFormat with the parameters supplied to this builder. 
*/ 
public TextFormat toTextFormat(); 
 
/** 
* Sets the text font. 
* @param font The desired font 
* @return This builder object to allow chaining calls 
*/ 
public TextFormatBuilder setFont(Font font); 
... 
```
