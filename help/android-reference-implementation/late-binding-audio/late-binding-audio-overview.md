---
description: Vous pouvez activer et créer des commandes pour le son de liaison tardive.
seo-description: Vous pouvez activer et créer des commandes pour le son de liaison tardive.
seo-title: Présentation
title: Présentation
uuid: 7656f930-f426-426e-bcd4-dfa9d39e7ae4
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Présentation {#overview}

Vous pouvez activer et créer des commandes pour le son de liaison tardive.

La norme HLS permet des flux multiformats, ce qui signifie que nous pouvons séparer les pistes audio et vidéo d’un flux les unes des autres. La piste vidéo, avec plusieurs rendus (p. ex., 240p, 480p, 720p et 1080p) et les pistes audio (p. ex., anglais, espagnol, français, allemand) peuvent être codées séparément. Le lecteur multimédia choisit ensuite les pistes vidéo et audio souhaitées et les relie à la volée, côté client.

Vous pouvez mettre en oeuvre divers  de, selon l’interface utilisateur du lecteur. Le flux de travail général du lecteur Primetime est le suivant :

1. Lorsque l’utilisateur final sélectionne une vidéo, un de pistes audio disponibles pour cet élément multimédia est renseigné.
1. Lorsque l’utilisateur touche le bouton Paramètres de l’interface utilisateur, les options de la piste audio s’affichent.
1. Lorsqu’une piste audio est sélectionnée, elle devient la piste audio active.
1. L’utilisateur final peut appuyer sur le bouton Paramètres pour revenir à la piste audio d’origine.

