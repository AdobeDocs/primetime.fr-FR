---
description: Vous pouvez spécifier la mise en forme des sous-titres.
seo-description: Vous pouvez spécifier la mise en forme des sous-titres.
seo-title: Exemples de formatage des légendes
title: Exemples de formatage des légendes
uuid: d55a506a-6662-4252-95f6-4073b2997f3b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Exemples : Formatage des légendes{#examples-caption-formatting}

Vous pouvez spécifier la mise en forme des sous-titres.

## Exemple 1 : Spécifier explicitement les valeurs de format {#section_BD7B48F3B66D4E9290E1CB2F464E08E4}

```js
// Set CC style. 
var tf = new AdobePSDK.TextFormat( 
      AdobePSDK.TextFormat.FONT_DEFAULT, 
      AdobePSDK.TextFormat.COLOR_DEFAULT, 
      AdobePSDK.TextFormat.COLOR_DEFAULT, 
      AdobePSDK.TextFormat.FONT_EDGE_DEFAULT, 
      AdobePSDK.TextFormat.COLOR_DEFAULT, 
      AdobePSDK.TextFormat.COLOR_DEFAULT, 
      AdobePSDK.TextFormat.SIZE_DEFAULT, 
      AdobePSDK.TextFormat.DEFAULT_OPACITY, 
      AdobePSDK.TextFormat.DEFAULT_OPACITY, 
      AdobePSDK.TextFormat.DEFAULT_OPACITY; 
 mediaPlayer.CCStyle(tf);
```

>[!IMPORTANT]
>
>Le SDK du navigateur ne prend pas en charge l’opacité des bords de police, des couleurs de fond ou des remplissages.

