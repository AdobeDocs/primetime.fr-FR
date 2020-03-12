---
description: Vous pouvez fournir des informations de style pour les pistes de sous-titrage à l’aide de la classe TextFormat, qui définit le style des sous-titrages à fermeture affichés par votre lecteur.
seo-description: Vous pouvez fournir des informations de style pour les pistes de sous-titrage à l’aide de la classe TextFormat, qui définit le style des sous-titrages à fermeture affichés par votre lecteur.
seo-title: Contrôle du style de sous-titrage
title: Contrôle du style de sous-titrage
uuid: b5d9c783-755f-47a2-acb1-966df9d6116e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Contrôle du style de sous-titrage {#control-closed-caption-styling}

Vous pouvez fournir des informations de style pour les pistes de sous-titrage à l’aide de la classe TextFormat, qui définit le style des sous-titrages à fermeture affichés par votre lecteur.

Cette classe encapsule les informations de style de sous-titrage, telles que le type, la taille, la couleur et l’opacité de l’arrière-plan.

## Définition des styles de sous-titrage {#section_C9B5E75C70DD42E59DC4DD0F308C8216}

Vous pouvez mettre en forme le texte de sous-titrage avec les méthodes TVSDK.

1. Attendez que le lecteur de médias soit au moins dans son `PREPARED` état.
1. Créez une `TextFormatBuilder` instance.

   Vous pouvez fournir maintenant tous les paramètres de style de sous-titrage ou les définir ultérieurement.

   TVSDK encapsule les informations de style de sous-titrage codé dans l’ `TextFormat` interface. La `TextFormatBuilder` classe crée des objets qui implémentent cette interface.

   ```java
   public TextFormatBuilder( 
      TextFormat.Font font, 
      TextFormat.Size size, 
      TextFormat.FontEdge fontEdge, 
      java.lang.String fontColor, 
      java.lang.String backgroundColor, 
      java.lang.String fillColor, 
      java.lang.String edgeColor, 
      int fontOpacity, 
      int backgroundOpacity, 
      int fillOpacity 
      java.lang.String bottomInset, 
      java.lang.String safeArea)
   ```

1. Pour obtenir une référence à un objet qui implémente l’ `TextFormat` interface, appelez la méthode `TextFormatBuilder.toTextFormat` publique.

   Cette opération renvoie un `TextFormat` objet qui peut être appliqué au lecteur de médias.

   `public TextFormat toTextFormat()`


1. Vous pouvez également obtenir les paramètres actuels du style de sous-titrage en procédant de l’une des manières suivantes :

   * Obtenez tous les paramètres de style avec `MediaPlayer.getCCStyle` La valeur renvoyée est une instance de l’ `TextFormat` interface.

      ```java
      /** 
      * @return the current closed captioning style.  
      * If no style was previously set, it returns a TextFormat object 
      * with default values for each attribute. 
      * @throws MediaPlayerException if media player was already released. 
      */ 
      public TextFormat getCCStyle() throws MediaPlayerException;
      ```

   * Obtenez les paramètres un par un grâce aux méthodes d’obtention de l’ `TextFormat` interface.

      ```java
      public java.lang.String getFontColor(); 
      public java.lang.String getBackgroundColor(); 
      public java.lang.String getFillColor(); // retrieve the font fill color 
      public java.lang.String getEdgeColor(); // retrieve the font edge color 
      public TextFormat.Size getSize(); // retrieve the font size 
      public TextFormat.FontEdge getFontEdge(); // retrieve the font edge type 
      public TextFormat.Font getFont(); // retrieve the font type 
      public int getFontOpacity(); 
      public int getBackgroundOpacity(); 
      public java.lang.String getBottomInset(java.lang.String bi); 
      public java.lang.String getSafeArea(java.lang.String sa);
      ```

1. Pour modifier les paramètres de style, effectuez l’une des opérations suivantes :

   * Utilisez la méthode setter `MediaPlayer.setCCStyle`, en transmettant une instance de l’ `TextFormat` interface :

      ```java
      /** 
      * Sets the closed captioning style. Used to control the closed captioning font, 
      * size, color, edge and opacity.  
      * 
      * This method is safe to use even if the current media stream doesn't have closed 
      * captions. 
      * 
      * @param textFormat 
      * @throws MediaPlayerException 
      */ 
      public void setCCStyle(TextFormat textFormat) throws MediaPlayerException;
      ```

   * Utilisez la `TextFormatBuilder` classe, qui définit des méthodes de définition individuelles.

      L’ `TextFormat` interface définit un objet immuable de sorte qu’il n’y ait que des méthodes get et pas de paramètres. Vous pouvez définir les paramètres de style de sous-titrage uniquement avec la `TextFormatBuilder` classe :

      ```java
      // set font type 
      public void setFont(Font font)  
      public void setBackgroundColor(String backgroundColor) 
      public void setFillColor(String fillColor) 
      // set the font-edge color 
      public void setEdgeColor(String edgeColor)  
      // set the font size 
      public void setSize(Size size)  
      // set the font edge type 
      public void setFontEdge(FontEdge fontEdge)  
      public void setFontOpacity(int fontOpacity) 
      public void setBackgroundOpacity(int backgroundOpacity) 
      // set the font-fill opacity level 
      public void setFillOpacity(int fillOpacity)  
      public void setFontColor(String fontColor) 
      public void setBottomInset(String bi) 
      public void setSafeArea(String sa) 
      public void setTreatSpaceAsAlphaNum(bool)
      ```

      [!IMPORTANT]

      **Paramètres de couleurs :** Dans Android TVSDK 2.X, une amélioration a été apportée au style colorimétrique des sous-titres codés. L’amélioration permet de définir les couleurs de sous-titrage à l’aide d’une chaîne hexadécimale représentant les valeurs de couleur RVB. La représentation des couleurs hexadécimales RVB est la chaîne de 6 octets que vous utilisez habituellement dans des applications telles que Photoshop :

          * FFFFF = Noir
          * 000000 = Blanc
          * FF0000 = Rouge
          * 00FF00 = Vert
          * 0000FF = Bleu
      etc.

      Dans votre application, chaque fois que vous transmettez des informations de style de couleur à `TextFormatBuilder`, vous utilisez toujours le `Color`  comme auparavant, mais vous devez maintenant ajouter `getValue()` à la couleur pour obtenir la valeur sous forme de chaîne. Par exemple :

      `tfb = tfb.setBackgroundColor(TextFormat.Color.RED      <b>.getValue()</b>);`


La définition du style de sous-titrage est une opération asynchrone. Les modifications peuvent donc prendre jusqu’à quelques secondes pour apparaître à l’écran.

## Options de style de sous-titrage {#section_6D685EC2D58C42A2BDDD574EDFCCC2A0}

Vous pouvez définir plusieurs options de style de légende, qui remplacent les options de style des légendes d’origine.

```java
public TextFormatBuilder( 
   Font font, 
   Size size, 
   FontEdge fontEdge, 
   String fontColor, 
   String backgroundColor, 
   String fillColor, 
   String edgeColor, 
   int fontOpacity, 
   int backgroundOpacity, 
   int fillOpacity,  
   String bottomInset 
   String safeArea)
```

>[!TIP]
>
>Dans les options qui définissent les valeurs par défaut (par exemple `DEFAULT`), cette valeur fait référence au paramètre défini lors de la spécification initiale de la légende.

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
   <td colname="2"> <p>Type de police. </p> <p>Peut uniquement être définie sur une valeur définie par le <span class="codeph"> TextFormat.Font </span> et qui représente, par exemple, un espacement fixe avec ou sans sérifs. </p> <p>Conseil :  Les polices disponibles sur un périphérique peuvent varier et des substitutions sont utilisées si nécessaire. Le monoespace avec empattements est généralement utilisé comme substitut, bien que cette substitution puisse être propre au système. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Taille </td> 
   <td colname="2"> <p>La taille de la légende. </p> <p> Peut uniquement être définie sur une valeur définie par le <span class="codeph"> TextFormat.Size </span> : 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM </span> - Taille standard </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> GRAND </span> - Environ 30 % plus grand que moyen </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> PETITE </span> - Environ 30 % inférieure à moyenne </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> DEFAULT </span> - Taille par défaut de la légende ; identique au support </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Bordure de la police </td> 
   <td colname="2"> <p>Effet utilisé pour le bord de la police, par exemple relevé ou aucun. </p> <p>Peut uniquement être définie sur une valeur définie par le <span class="codeph"> TextFormat.FontEdge </span> . </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Couleur de police </td> 
   <td colname="2"> <p>Couleur de la police. </p> <p>Peut uniquement être définie sur une valeur définie par le <span class="codeph"> TextFormat.Color </span> . </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Couleur du bord </td> 
   <td colname="2"> <p>Couleur de l’effet de contour. </p> <p>Peut être définie sur l’une des valeurs disponibles pour la couleur de la police. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Couleur d'arrière-plan </td> 
   <td colname="2"> <p>Couleur de la cellule du caractère d’arrière-plan. </p> <p>Peut uniquement être définie sur des valeurs disponibles pour la couleur de la police. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Couleur de remplissage </td> 
   <td colname="2"> <p>Couleur d’arrière-plan de la fenêtre dans laquelle se trouve le texte. </p> <p>Peut être définie sur l’une des valeurs disponibles pour la couleur de la police. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Opacité de la police </td> 
   <td colname="2"> <p>Opacité du texte. </p> <p>Exprimé en pourcentage de 0 (entièrement transparent) à 100 (entièrement opaque). <span class="codeph"> DEFAULT_OPACITY </span> pour la police est 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Opacité du fond </td> 
   <td colname="2"> <p>Opacité de la cellule de caractère d’arrière-plan. </p> <p>Exprimé en pourcentage de 0 (entièrement transparent) à 100 (entièrement opaque). <span class="codeph"> DEFAULT_OPACITY </span> pour l’arrière-plan est 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Opacité du remplissage </td> 
   <td colname="2"> <p>Opacité de l’arrière-plan de la fenêtre de sous-titrage. </p> <p>Exprimé en pourcentage de 0 (entièrement transparent) à 100 (entièrement opaque). <span class="codeph"> DEFAULT_OPACITY </span> pour le remplissage est égal à 0. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Encart inférieur </td> 
   <td colname="2"> <p>Distance verticale par rapport au bas de la fenêtre de sous-titrage pour que les légendes soient évitées. </p> <p>Exprimé sous forme de pourcentage de la hauteur de la fenêtre de sous-titrage (par exemple, "20 %") ou d’un nombre de pixels (par exemple, "20"). </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> Zone sécurisée </td> 
   <td colname="2"> <p>Zone située autour du bord de l’écran, entre 0 % et 25 %, où les légendes n’apparaissent pas. </p> <p>Par défaut, la zone de sécurité pour WebVTT est de 0 %. Ce paramètre permet à votre application de remplacer cette valeur par défaut. Si deux valeurs sont fournies, par exemple, la chaîne "10 %,20 %", la première valeur est la zone horizontale sécurisée et la seconde, la zone verticale sécurisée. Si une valeur est fournie, par exemple, la chaîne "15 %", les axes vertical et horizontal utilisent tous deux la zone sécurisée spécifiée. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Exemples de formatage des légendes {#section_58E8E82494EC4683B010FFDE67485CF9}

Voici quelques exemples qui vous montrent comment définir le formatage des sous-titres.

```java
private final MediaPlayer.PlaybackEventListener _playbackEventListener = 
  new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() { 
        // Set CC style. 
        TextFormat tf = new TextFormatBuilder( 
            TextFormat.Font.DEFAULT, 
            TextFormat.Size.DEFAULT, 
            TextFormat.FontEdge.DEFAULT, 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.DEFAULT_OPACITY, 
            TextFormat.DEFAULT_OPACITY, 
            TextFormat.DEFAULT_OPACITY).toTextFormat(); 
 
        mediaPlayer.setCCStyle(tf); 
        ... 
    } 
} 
```

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
public  
<b>TextFormatBuilder</b>( 
    Font font, Size size, FontEdge fontEdge, 
    String fontColor, String backgroundColor,  
    String fillColor, String edgeColor, 
    int fontOpacity, int backgroundOpacity, 
    int fillOpacity); 
/** 
* Creates a TextFormat with the parameters supplied to this builder. 
*/ 
public TextFormat  
<b>toTextFormat</b>(); 
/** 
* Sets the text font. 
* @param font The desired font 
* @return This builder object to allow chaining calls 
*/ 
public  
<b>TextFormatBuilder</b> setFont(Font font); 
...
```

