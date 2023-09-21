---
description: Le serveur de manifeste prend en charge les sous-titres WebVTT activés par l’éditeur pour tous les formats vidéo HLS. Lorsqu’il reçoit des demandes d’insertion de publicités dans le contenu sous-titré de WebVTT, il le fait correctement.
title: Prise en charge des sous-titres WebVTT
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Prise en charge des sous-titres WebVTT {#support-for-webvtt-captions}

Le serveur de manifeste prend en charge les sous-titres WebVTT activés par l’éditeur pour les formats vidéo HLS/DASH. Lorsqu’il reçoit des demandes d’insertion de publicités dans le contenu sous-titré de WebVTT, il le fait correctement.

Si l’éditeur inclut des sous-titres WebVTT dans le contenu, le serveur de manifeste envoie au client un flux de contenu avec des sous-titres. WebVTT doit être activé par l’éditeur pour que le serveur de manifeste prenne en charge les sous-titres. Lorsque les sous-titres WebVTT sont activés pour le client et qu’il envoie une requête au serveur de manifeste, ce dernier manipule la chronologie et le suivi WebVTT, puis renvoie au client le contenu contenant des publicités et des sous-titres assemblés.

Le workflow des flux de contenu VOD est le suivant :

1. Le client envoie un flux de contenu avec des sous-titres WebVTT activés sur le serveur de manifeste.
1. Le serveur de manifeste manipule la chronologie pour regrouper des publicités dans le flux de contenu.
1. Le serveur de manifeste manipule le suivi WebVTT pour ajouter des sous-titres au contenu (y compris les publicités).
1. Le serveur de manifeste diffuse le flux de contenu au client, avec les publicités et légendes insérées.

>[!NOTE]
>
>Si un segment de légende WebVTT se trouve dans une publicité mid-roll, le lecteur voit cette légende jouer avant et après cette coupure publicitaire mid-roll. Par exemple, dans un segment de sous-titrage de 10 secondes avec une publicité mid-roll de 30 secondes à l’indicateur de 5 secondes, la visionneuse voit ce segment de sous-titrage pendant 5 secondes avant la coupure publicitaire mid-roll et pendant 5 secondes après la coupure publicitaire mid-roll.

>[!NOTE]
>
>Si un client demande qu’une vidéo soit lue dans une langue spécifique telle que l’anglais, puis demande de lire la vidéo en français, le serveur de manifeste ne peut pas détecter que le client a demandé de modifier la langue en français. Comme le client ne communique pas avec le serveur de manifeste, le serveur de manifeste insère la légende de publicité dans le flux vidéo en utilisant la première langue spécifiée dans le fichier maître M3U8 de la publicité.
