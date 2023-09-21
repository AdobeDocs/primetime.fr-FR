---
description: Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge de l’enregistrement numérique (DVR) pour la diffusion VOD et la diffusion en direct. La prise en charge de l’enregistrement numérique (DVR) comprend le concept de fenêtre pouvant faire l’objet d’une recherche et le point d’activation du client.
title: Création d’une barre de contrôle améliorée pour le contrôle DVR
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Création d’une barre de contrôle améliorée pour le contrôle DVR{#construct-a-control-bar-enhanced-for-dvr}

Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge de l’enregistrement numérique (DVR) pour la diffusion VOD et la diffusion en direct. La prise en charge de l’enregistrement numérique (DVR) comprend le concept de fenêtre pouvant faire l’objet d’une recherche et le point d’activation du client.

* Pour VOD, la durée de la fenêtre pouvant faire l’objet d’une recherche correspond à la durée de la ressource entière.
* Pour la diffusion en direct en continu, la durée de la fenêtre de l’enregistreur numérique (lisible) est définie comme la période qui s’étend de la fenêtre de lecture en direct à la fenêtre de lecture en direct et qui se termine au point d’entrée en direct du client.

  Le point d’activation du client est calculé en soustrayant la longueur mise en mémoire tampon de la fin de la fenêtre active. La durée cible est une valeur supérieure ou égale à la durée maximale d’un fragment dans le manifeste.

  La barre de contrôle de la lecture en direct prend en charge la réalité virtuelle en premier lieu positionnant le curseur au point d’exécution client lors du démarrage de la lecture et en affichant une région qui marque la zone où la recherche n’est pas autorisée.

Pour une barre de contrôle :

1. Ajoutez une superposition à la barre de contrôle qui représente la plage de lecture.

1. Lorsque l’utilisateur commence la recherche, vérifiez si la position de la recherche souhaitée se trouve dans la plage pouvant faire l’objet d’une recherche.
