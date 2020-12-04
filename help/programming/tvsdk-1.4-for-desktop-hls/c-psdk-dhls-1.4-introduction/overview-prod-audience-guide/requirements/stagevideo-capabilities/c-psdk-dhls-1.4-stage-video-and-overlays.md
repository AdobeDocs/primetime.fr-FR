---
description: Vous pouvez utiliser des incrustations HTML avec StageVideo pour afficher des éléments d’interface dans le plan vidéo de la liste d’affichage du Flash. Ce plan se trouve au-dessus du plan StageVideo, de sorte que StageVideo s’affiche toujours derrière n’importe quel élément de liste d’affichage de Flash.
seo-description: Vous pouvez utiliser des incrustations HTML avec StageVideo pour afficher des éléments d’interface dans le plan vidéo de la liste d’affichage du Flash. Ce plan se trouve au-dessus du plan StageVideo, de sorte que StageVideo s’affiche toujours derrière n’importe quel élément de liste d’affichage de Flash.
seo-title: Incrustations StageVideo et HTML
title: Incrustations StageVideo et HTML
uuid: 84e862ab-4c35-47a2-9c4e-f792d3ef5363
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Incrustations StageVideo et HTML{#stagevideo-and-html-overlays}

Vous pouvez utiliser des incrustations HTML avec StageVideo pour afficher des éléments d’interface dans le plan vidéo de la liste d’affichage du Flash. Ce plan se trouve au-dessus du plan StageVideo, de sorte que StageVideo s’affiche toujours derrière n’importe quel élément de liste d’affichage de Flash.

Les incrustations HTML sont des éléments de l’interface utilisateur que vous pouvez afficher dans le plan d’affichage du Flash sur une vidéo rendue par `StageVideo` sur son propre plan. Avant le Flash 15, vous ne pouviez pas utiliser d’incrustations HTML lorsque l’accélération matérielle n’était pas disponible. À partir du Flash 15, les incrustations HTML s’affichent lorsque `StageVideo` revient au rendu logiciel.

>[!IMPORTANT]
>
>En fonction des capacités de votre système, les performances peuvent se dégrader à un degré supérieur ou inférieur lorsque vous utilisez des incrustations HTML.

Tenez compte des informations suivantes :

* Au Flash Player 15 :

   * Vous pouvez utiliser des incrustations HTML pour déterminer si l’accélération matérielle est disponible.
   * Pour utiliser des incrustations HTML, définissez `wmode` sur `opaque`.

* Au Flash Player 14 :

   * Lorsque l’accélération matérielle est disponible, `StageVideo` se trouve sous la liste d’affichage du Flash, ce qui vous permet d’utiliser des incrustations HTML.
   * Lorsque l’accélération matérielle n’est pas disponible, la vidéo est générée par-dessus tous les autres éléments du navigateur, ce qui empêche l’utilisation d’incrustations HTML.

Voici la configuration minimale requise pour le navigateur pour utiliser des incrustations HTML avec `StageVideo` :

* Firefox version 4 ou ultérieure
* Safari version 4 et ultérieure
* Internet Explorer :

   * Version 9+ sous Windows 7 et versions ultérieures
   * Version 10+ sous Windows XP

* Chrome version 26 et ultérieure

   >[!IMPORTANT]
   >
   >Chrome Pepper sous Windows XP et Windows Vista n’est pas pris en charge.

