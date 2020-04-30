---
description: Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge du DVR pour la diffusion VOD et en direct. Le support DVR inclut le concept d'une fenêtre pouvant être recherchée et le point de vie du client.
seo-description: Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge du DVR pour la diffusion VOD et en direct. Le support DVR inclut le concept d'une fenêtre pouvant être recherchée et le point de vie du client.
seo-title: Construire une barre de contrôle améliorée pour le magnétoscope numérique
title: Construire une barre de contrôle améliorée pour le magnétoscope numérique
uuid: 83c56def-a454-4f26-bdfc-2ef2497ef9bd
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Construire une barre de contrôle améliorée pour le magnétoscope numérique{#construct-a-control-bar-enhanced-for-dvr}

Vous pouvez mettre en oeuvre une barre de contrôle avec la prise en charge du DVR pour la diffusion VOD et en direct. Le support DVR inclut le concept d&#39;une fenêtre pouvant être recherchée et le point de vie du client.

* Pour VOD, la longueur de la fenêtre pouvant faire l’objet d’une recherche correspond à la durée de la ressource entière.
* Pour la diffusion en continu en direct, la longueur de la fenêtre du DVR (pouvant être recherchée) est définie comme la plage de temps qui commence à la fenêtre de lecture en direct et se termine au point de lecture client.

   Le point d&#39;activation du client est calculé en soustrayant la longueur mise en mémoire tampon de l&#39;extrémité de la fenêtre active. La durée de la cible est une valeur supérieure ou égale à la durée maximale d’un fragment dans le manifeste.

   La barre de contrôle de la lecture en direct prend en charge le magnétoscope numérique en positionnant d’abord le pouce au point de lecture client lors du démarrage de la lecture et en affichant une région qui marque la zone où la recherche n’est pas autorisée.

Pour une barre de contrôle :

1. Ajouter une incrustation sur la barre de contrôle qui représente la plage de lecture.

1. Lorsque l’utilisateur début effectuer une recherche, vérifiez si la position de recherche souhaitée se trouve dans la plage recherchée.
