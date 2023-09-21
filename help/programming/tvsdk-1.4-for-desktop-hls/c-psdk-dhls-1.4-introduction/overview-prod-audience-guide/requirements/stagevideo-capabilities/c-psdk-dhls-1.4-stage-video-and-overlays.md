---
description: Vous pouvez utiliser des incrustations de HTML avec StageVideo pour afficher les éléments de l’interface utilisateur dans le plan vidéo de la liste d’affichage des Flashs. Ce plan se trouve au-dessus du plan StageVideo. StageVideo s’affiche donc toujours derrière les éléments de la liste d’affichage de Flash.
title: Superpositions de HTMLS et de vidéos dans l’environnement intermédiaire
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Superpositions de HTMLS et de vidéos dans l’environnement intermédiaire{#stagevideo-and-html-overlays}

Vous pouvez utiliser des incrustations de HTML avec StageVideo pour afficher les éléments de l’interface utilisateur dans le plan vidéo de la liste d’affichage des Flashs. Ce plan se trouve au-dessus du plan StageVideo. StageVideo s’affiche donc toujours derrière les éléments de la liste d’affichage de Flash.

Les incrustations de HTML sont des éléments de l’interface utilisateur que vous pouvez afficher dans le plan d’affichage de Flash sur une vidéo rendue par `StageVideo` dans son propre avion. Avant le Flash 15, vous ne pouviez pas utiliser de superpositions de HTML lorsque l’accélération matérielle n’était pas disponible. À partir du Flash 15, les superpositions par HTML s’affichent lorsque `StageVideo` revient au rendu logiciel.

>[!IMPORTANT]
>
>Selon les fonctionnalités de votre système, les performances peuvent se dégrader plus ou moins fortement lorsque vous utilisez des incrustations de HTML.

Tenez compte des informations suivantes :

* Dans le Flash Player 15 :

   * Vous pouvez utiliser des incrustations de HTML pour déterminer si l’accélération matérielle est disponible.
   * Pour utiliser des incrustations de HTML, définissez `wmode` to `opaque`.

* Dans le Flash Player 14 :

   * Lorsque l’accélération matérielle est disponible, `StageVideo` se trouve sous la liste d’affichage des Flashs afin que vous puissiez utiliser des superpositions de HTML.
   * Lorsque l’accélération matérielle n’est pas disponible, la vidéo s’affiche au-dessus de tous les autres éléments du navigateur, ce qui empêche l’utilisation d’incrustations de HTML.

Voici la configuration minimale requise du navigateur pour utiliser des incrustations de HTML avec `StageVideo`:

* Firefox version 4 et ultérieure
* Safari version 4 et ultérieure
* Internet Explorer :

   * Version 9+ sous Windows 7 et versions ultérieures
   * Version 10+ sous Windows XP

* Chrome version 26 et ultérieure

  >[!IMPORTANT]
  >
  >Chrome Pepper sous Windows XP et Windows Vista n’est pas pris en charge.
