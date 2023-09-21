---
description: Vous pouvez définir le format, tel que la police, la taille, la couleur, le bord et l’opacité du texte sous-titrage.
title: Définition des styles de sous-titres fermés
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Définition des styles de sous-titres fermés{#set-closed-caption-styles}

Vous pouvez définir le format, tel que la police, la taille, la couleur, le bord et l’opacité du texte sous-titrage.

1. Attendez que la variable `MediaPlayer` soit au moins à l’état PRÉPARÉ .

   Pour plus d’informations sur les états, voir [Attente d’un état valide](../../../content-playback-options-browser-tvsdk/ui-configure/t-psdk-browser-tvsdk-2.4-ui-state-prepared-wait-for.md).
1. Créez un `TextFormat` instance.

   Vous pouvez désormais fournir tous les paramètres de style de sous-titres ou les définir ultérieurement.

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
       bottomInset 
       safeArea) → {AdobePSDK.TextFormat}
   ```

1. (Facultatif) Obtenez les paramètres actuels de style de sous-titres avec `MediaPlayer.ccStyle`.

   La valeur renvoyée est une instance de la variable `TextFormat` .

   Si aucun style n’a été précédemment défini, elle renvoie un objet TextFormat avec les valeurs par défaut pour chaque attribut :

   ```js
   ccStyle :AdobePSDK.TextFormat
   ```

1. Pour modifier les paramètres de style, utilisez `MediaPlayer.ccStyle`, en transmettant une instance de la fonction `TextFormat` .

   Vous pouvez utiliser cette méthode même si le flux multimédia actuel ne comporte pas de sous-titres non intégrés.

   ```js
   ccStyle :AdobePSDK.TextFormat 
   ```

   >[!TIP]
   >
   >La définition du style de sous-titrage codé est asynchrone. Les modifications peuvent donc prendre quelques secondes pour s’afficher à l’écran.
