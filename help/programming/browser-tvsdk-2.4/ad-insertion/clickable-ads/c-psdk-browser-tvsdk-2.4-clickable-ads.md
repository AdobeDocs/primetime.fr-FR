---
description: Le navigateur TVSDK fournit à votre application vidéo les informations nécessaires pour répondre au clic d’un utilisateur sur une publicité cliquable.
title: Publicités cliquables
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Présentation {#clickable-ads-overview}

Le navigateur TVSDK fournit à votre application vidéo les informations nécessaires pour répondre au clic d’un utilisateur sur une publicité cliquable.

Lorsqu’un utilisateur clique sur une publicité cliquable, une réponse standard d’une application vidéo consiste à ouvrir une nouvelle fenêtre de navigateur et à accéder à l’URL associée à la publicité. Pour faciliter cette opération, le navigateur TVSDK déclenche des notifications que votre application peut utiliser pour gérer le processus de clic publicitaire.

Dans votre application, vous pouvez fournir à l’utilisateur un contrôle pour qu’il clique (par exemple, un bouton) pendant la lecture de la publicité cliquable. Vous devez créer des gestionnaires pour les événements déclenchés par le Browser TVSDK associés à la publicité (par exemple, démarrage de publicité, clic sur la publicité, fin de publicité). Enfin, vous devez mettre en oeuvre les comportements spécifiques que votre application suivra lors du clic publicitaire d’un utilisateur (par exemple, si vous souhaitez suspendre la publicité, afficher l’URL du clic publicitaire, etc.).

>[!NOTE]
>
>Le lecteur de référence inclus dans le Browser TVSDK comprend une solution opérationnelle possible pour le traitement des publicités avec clics publicitaires.
