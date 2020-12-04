---
description: Vous pouvez définir le format, tel que la police, la taille, la couleur, le bord et l’opacité du texte de sous-titrage.
seo-description: Vous pouvez définir le format, tel que la police, la taille, la couleur, le bord et l’opacité du texte de sous-titrage.
seo-title: Définition des styles de sous-titrage
title: Définition des styles de sous-titrage
uuid: 906ed22c-e673-4211-a14b-d95d176aad21
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Définir les styles de sous-titrage{#set-closed-caption-styles}

Vous pouvez définir le format, tel que la police, la taille, la couleur, le bord et l’opacité du texte de sous-titrage.

1. Attendez que `MediaPlayer` soit au moins à l’état PRÉPARÉ.

   Pour plus d’informations sur les états, voir [Attendre un état valide](../../../content-playback-options-browser-tvsdk/ui-configure/t-psdk-browser-tvsdk-2.4-ui-state-prepared-wait-for.md).
1. Créez une instance `TextFormat`.

   Vous pouvez fournir tous les paramètres de style de sous-titrage ou les définir ultérieurement.

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

1. (Facultatif) Obtenez les paramètres actuels du style de sous-titrage avec `MediaPlayer.ccStyle`.

   La valeur renvoyée est une instance de l&#39;interface `TextFormat`.

   Si aucun style n’a été précédemment défini, il renvoie un objet TextFormat avec des valeurs par défaut pour chaque attribut :

   ```js
   ccStyle :AdobePSDK.TextFormat
   ```

1. Pour modifier les paramètres de style, utilisez `MediaPlayer.ccStyle`, en transmettant une instance de l&#39;interface `TextFormat`.

   Vous pouvez utiliser cette méthode même si le flux média actuel ne comporte pas de sous-titres fermés.

   ```js
   ccStyle :AdobePSDK.TextFormat 
   ```

   >[!TIP]
   >
   >La définition du style de sous-titrage est asynchrone. Il peut donc s’écouler quelques secondes avant que les modifications ne s’affichent à l’écran.

