---
description: Vous pouvez activer et créer des commandes pour les fichiers audio à liaison tardive.
seo-description: Vous pouvez activer et créer des commandes pour les fichiers audio à liaison tardive.
seo-title: Présentation
title: Présentation
uuid: 7656f930-f426-426e-bcd4-dfa9d39e7ae4
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---


# Aperçu {#overview}

Vous pouvez activer et créer des commandes pour les fichiers audio à liaison tardive.

La norme HLS permet des flux multiformats, ce qui signifie que nous pouvons séparer les pistes audio et vidéo d&#39;un flux les unes des autres. La piste vidéo, avec plusieurs rendus (p. ex., 240p, 480p, 720p et 1080p) et les pistes audio (p. ex., anglais, espagnol, français, allemand) peuvent être codées séparément. Le lecteur multimédia choisit ensuite les pistes vidéo et audio de votre choix et les relie à la volée, côté client.

Vous pouvez mettre en oeuvre divers workflows, en fonction de l’interface utilisateur du lecteur. Le flux de travail général du lecteur Primetime est le suivant :

1. Lorsque l&#39;utilisateur final sélectionne une vidéo, une liste de pistes audio disponibles pour cet élément multimédia est renseignée.
1. Lorsque l’utilisateur touche le bouton Paramètres de l’interface utilisateur, les options de la piste audio s’affichent.
1. Lorsqu’une piste audio est sélectionnée, elle devient la principale piste audio.
1. L’utilisateur final peut appuyer sur le bouton Paramètres pour revenir à la piste audio d’origine.

