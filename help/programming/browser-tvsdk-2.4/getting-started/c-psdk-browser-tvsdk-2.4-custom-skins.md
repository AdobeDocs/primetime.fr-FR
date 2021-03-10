---
description: Pour utiliser les habillages personnalisés, vous devez écrire la personnalisation semblable à default-video-control.css et faire référence à cette nouvelle personnalisation dans le lecteur.
title: Habillages personnalisés
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Habillages personnalisés{#custom-skins}

Pour utiliser les habillages personnalisés, vous devez écrire la personnalisation semblable à default-video-control.css et faire référence à cette nouvelle personnalisation dans le lecteur.

Par exemple, vous pouvez utiliser l’une des options suivantes :

* `<link rel="stylesheet" href="css/common_style.css">`
* `<link rel="stylesheet" href="css/custom-video-controls1.css">`

Vous pouvez effectuer les types de modifications suivants :

* Couleur de premier plan des boutons et du texte

   Tous les contrôles qui ont un premier plan utilisent la classe `vid-skin-fgcolor`. Pour modifier le premier plan de tous les contrôles, effectuez une itération sur tous les éléments avec la classe `vid-skin-fgcolor` et spécifiez la couleur souhaitée.
* Couleur d’arrière-plan des boutons et du texte

   Tous les contrôles avec un premier plan utilisent la classe `vid-skin-bgcolor`. Pour modifier le premier plan de tous les contrôles, effectuez une itération sur tous les éléments avec la classe `vid-skin-bgcolor` et spécifiez la couleur souhaitée.
* Forme de la tête de jeu

   La tête de jeu peut être carrée ou ronde. Pour modifier la tête de lecture, ajoutez la classe `square` ou `round` à l’élément `playhead`.
* Style des spinners de mise en mémoire tampon

   Le lecteur de référence fournit les styles suivants de moteurs de balayage qui peuvent être affichés lorsque le lecteur met en mémoire tampon le contenu :

   * Texte de l’incrustation ( `overlay-text`)
   * Spinteur rectangulaire ( `spinner`)
   * Signal ( `signal`)
   * Barres verticales ( `vertical`)

      >[!TIP]
      >
      >Pour utiliser l&#39;une des versions de mise en mémoire tampon, vous devez ajouter la classe dans l&#39;élément de mise en mémoire tampon-recouvrement. Par exemple, pour utiliser `overlay-text`, ajoutez les lignes suivantes dans le fichier `BufferOverlay.js` :
      >
      >
      ```js
      >var overlay = document.getElementById("buffering-overlay"); 
      >overlay.classList.add ("spinner");
      >```

