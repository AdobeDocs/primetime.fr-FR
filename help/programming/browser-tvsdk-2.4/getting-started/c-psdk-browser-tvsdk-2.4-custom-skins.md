---
description: Pour utiliser les habillages personnalisés, vous devez écrire la personnalisation semblable à default-video-control.css et faire référence à cette nouvelle personnalisation dans le lecteur.
title: habillages personnalisés
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# habillages personnalisés{#custom-skins}

Pour utiliser les habillages personnalisés, vous devez écrire la personnalisation semblable à default-video-control.css et faire référence à cette nouvelle personnalisation dans le lecteur.

Par exemple, vous pouvez utiliser l’une des options suivantes :

* `<link rel="stylesheet" href="css/common_style.css">`
* `<link rel="stylesheet" href="css/custom-video-controls1.css">`

Vous pouvez effectuer les types de modifications suivants :

* Couleur de premier plan des boutons et du texte

  Tous les contrôles qui ont un premier plan utilisent le `vid-skin-fgcolor` classe . Pour modifier le premier plan de tous les contrôles, effectuez une itération sur tous les éléments avec la propriété `vid-skin-fgcolor` et spécifiez la couleur souhaitée.
* Couleur d’arrière-plan des boutons et du texte

  Tous les contrôles qui ont un premier plan utilisent le `vid-skin-bgcolor` classe . Pour modifier le premier plan de tous les contrôles, effectuez une itération sur tous les éléments avec la commande `vid-skin-bgcolor` et spécifiez la couleur souhaitée.
* Forme de la tête de jeu

  La tête de la pièce peut être carrée ou ronde. Pour modifier la tête de lecture, ajoutez `square` ou `round` à `playhead` élément .
* Style des coins de mise en mémoire tampon

  Le lecteur de référence fournit les styles de compteur suivants qui peuvent être affichés lorsque le lecteur met en mémoire tampon le contenu :

   * Texte de la superposition ( `overlay-text`)
   * Rotation rectangulaire ( `spinner`)
   * Signal ( `signal`)
   * Barres verticales ( `vertical`)

     >[!TIP]
     >
     >Pour utiliser l’un des volets de mise en mémoire tampon, vous devez ajouter la classe dans l’élément de mise en mémoire tampon-recouvrement. Par exemple, pour utiliser `overlay-text`, ajoutez les lignes suivantes dans le `BufferOverlay.js` fichier :
     >
     >```js
     >var overlay = document.getElementById("buffering-overlay"); 
     >overlay.classList.add ("spinner");
     >```
     >
