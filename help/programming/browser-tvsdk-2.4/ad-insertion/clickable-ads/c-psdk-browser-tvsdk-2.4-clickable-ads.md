---
description: Le navigateur TVSDK fournit à votre application vidéo les informations nécessaires pour répondre aux clics d’un utilisateur sur une publicité cliquable.
seo-description: Le navigateur TVSDK fournit à votre application vidéo les informations nécessaires pour répondre aux clics d’un utilisateur sur une publicité cliquable.
seo-title: Publicités cliquables
title: Publicités cliquables
uuid: 493c3199-b5ba-4809-86eb-e80f10eb957b
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Présentation {#clickable-ads-overview}

Le navigateur TVSDK fournit à votre application vidéo les informations nécessaires pour répondre aux clics d’un utilisateur sur une publicité cliquable.

Lorsqu’un utilisateur clique sur une publicité cliquable, une réponse standard d’une application vidéo consiste à ouvrir une nouvelle fenêtre de navigateur et à accéder à l’URL associée à la publicité. Pour faciliter cette tâche, le navigateur TVSDK déclenche des notifications que votre application peut utiliser pour gérer le processus de clics publicitaires.

Dans votre application, vous pouvez fournir à l’utilisateur un contrôle lui permettant de cliquer (par exemple, un bouton) pendant la lecture de la publicité cliquable. Vous devez créer des gestionnaires pour les événements déclenchés par le navigateur TVSDK qui sont associés à la publicité (par exemple, début publicitaire, clic publicitaire, publicité terminée). Enfin, vous devez mettre en oeuvre les comportements spécifiques que votre application suivra lors du clic publicitaire d’un utilisateur (par exemple, pour suspendre ou non la publicité, afficher l’URL de clic publicitaire, etc.).

>[!NOTE]
>
>Le lecteur de référence inclus dans le SDK du navigateur inclut une solution de fonctionnement possible pour le traitement des publicités par clics publicitaires.