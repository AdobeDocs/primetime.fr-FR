---
description: Vous pouvez activer et créer des contrôles pour le contenu audio de liaison tardive.
title: Présentation
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Présentation {#overview}

Vous pouvez activer et créer des contrôles pour le contenu audio de liaison tardive.

La norme HLS permet des flux multiformats, ce qui signifie que nous pouvons séparer les pistes audio et vidéo d’un flux les unes des autres. La piste vidéo, avec plusieurs rendus (par exemple, 240p, 480p, 720p et 1 080p) et les pistes audio (par exemple, anglais, espagnol, français, allemand) peuvent être codées séparément. Le lecteur multimédia choisit ensuite les pistes vidéo et audio souhaitées et les associe à la volée, côté client.

Vous pouvez mettre en oeuvre différents workflows en fonction de l’interface utilisateur de votre lecteur. Le workflow général du lecteur Primetime est le suivant :

1. Lorsque l’utilisateur final sélectionne une vidéo, une liste des pistes audio disponibles pour cet élément multimédia est renseignée.
1. Lorsque l’utilisateur clique sur le bouton Paramètres de l’interface utilisateur, les options de suivi audio s’affichent.
1. Lorsqu’une piste audio est sélectionnée, elle devient la piste audio active.
1. L’utilisateur final peut appuyer sur le bouton Paramètres pour revenir à la piste audio d’origine.
