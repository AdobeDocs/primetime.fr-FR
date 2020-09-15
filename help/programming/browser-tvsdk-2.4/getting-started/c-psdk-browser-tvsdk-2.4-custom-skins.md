---
description: Pour utiliser les habillages personnalisés, vous devez écrire la personnalisation semblable à default-video-control.css et faire référence à cette nouvelle personnalisation dans le lecteur.
seo-description: Pour utiliser les habillages personnalisés, vous devez écrire la personnalisation semblable à default-video-control.css et faire référence à cette nouvelle personnalisation dans le lecteur.
seo-title: Habillages personnalisés
title: Habillages personnalisés
uuid: bc71926e-0dec-4628-8248-911224a7a6c2
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# Habillages personnalisés{#custom-skins}

Pour utiliser les habillages personnalisés, vous devez écrire la personnalisation semblable à default-video-control.css et faire référence à cette nouvelle personnalisation dans le lecteur.

Par exemple, vous pouvez utiliser l’une des options suivantes :

* `<link rel="stylesheet" href="css/common_style.css">`
* `<link rel="stylesheet" href="css/custom-video-controls1.css">`

Vous pouvez effectuer les types de modifications suivants :

* Couleur de premier plan des boutons et du texte

   Tous les contrôles qui ont un premier plan utilisent la `vid-skin-fgcolor` classe. Pour modifier le premier plan de tous les contrôles, effectuez une itération sur tous les éléments de la `vid-skin-fgcolor` classe et spécifiez la couleur souhaitée.
* Couleur d’arrière-plan des boutons et du texte

   Tous les contrôles qui ont un premier plan utilisent la `vid-skin-bgcolor` classe. Pour modifier le premier plan de tous les contrôles, effectuez une itération sur tous les éléments avec `vid-skin-bgcolor` classe et spécifiez la couleur souhaitée.
* Forme de la tête de jeu

   La tête de jeu peut être carrée ou ronde. Pour modifier la tête de lecture, ajoutez `square` ou `round` la classe à `playhead` l’élément.
* Style des spinners de mise en mémoire tampon

   Le lecteur de référence fournit les styles suivants de moteurs de balayage qui peuvent être affichés lorsque le lecteur met en mémoire tampon le contenu :

   * Texte de l’incrustation ( `overlay-text`)
   * Spinteur rectangulaire ( `spinner`)
   * Signal ( `signal`)
   * Barres verticales ( `vertical`)

      >[!TIP]
      >
      >Pour utiliser l&#39;une des versions de mise en mémoire tampon, vous devez ajouter la classe dans l&#39;élément de mise en mémoire tampon-recouvrement. Par exemple, pour utiliser `overlay-text`, ajoutez les lignes suivantes dans le `BufferOverlay.js` fichier :
      >
      >
      ```js
      >var overlay = document.getElementById("buffering-overlay"); 
      >overlay.classList.add ("spinner");
      >```

