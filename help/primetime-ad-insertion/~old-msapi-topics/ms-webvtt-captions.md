---
description: Le serveur de manifeste prend en charge les légendes WebVTT activées pour l’éditeur pour tous les formats vidéo HLS. Lorsqu’il reçoit des demandes d’insertion de publicités dans le contenu sous-titré WebVTT, il le fait correctement.
seo-description: Le serveur de manifeste prend en charge les légendes WebVTT activées pour l’éditeur pour tous les formats vidéo HLS/DASH. Lorsqu’il reçoit des demandes d’insertion de publicités dans le contenu sous-titré WebVTT, il le fait correctement.
seo-title: Prise en charge des légendes WebVTT
title: Prise en charge des légendes WebVTT
uuid: 1dc728b0-5aeb-4c48-8f3b-54ff4b135742
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---


# Prise en charge des légendes WebVTT {#support-for-webvtt-captions}

Le serveur de manifeste prend en charge les légendes WebVTT activées par l’éditeur pour les formats vidéo HLS/DASH. Lorsqu’il reçoit des demandes d’insertion de publicités dans le contenu sous-titré WebVTT, il le fait correctement.

Si l’éditeur inclut des légendes WebVTT dans le contenu, le serveur de manifeste envoie au client un flux de contenu avec des légendes. WebVTT doit être activé par l’éditeur pour que le serveur de manifeste prenne en charge les légendes. Lorsque les légendes WebVTT sont activées pour le client et qu’une requête est envoyée au serveur de manifeste, le serveur de manifeste manipule la chronologie et le suivi WebVTT et renvoie au client le contenu avec des publicités et légendes assemblées.

Le processus des flux de contenu VOD est le suivant :

1. Le client envoie un flux de contenu avec des légendes WebVTT activées sur le serveur de manifeste.
1. Le serveur de manifeste manipule la chronologie pour associer des publicités au flux de contenu.
1. Le serveur de manifeste manipule le suivi WebVTT pour ajouter des légendes au contenu (y compris les publicités).
1. Le serveur de manifeste diffuse le flux de contenu au client, avec les publicités et légendes insérées.

>[!NOTE]
>
>Si un segment de sous-titrage WebVTT se trouve dans une publicité preroll mid-roll, le lecteur voit cette légende jouer avant et après cette coupure publicitaire mid-roll. Par exemple, dans un segment de sous-titrage de 10 secondes avec une publicité à mi-parcours de 30 secondes à la marque de 5 secondes, le lecteur voit ce segment de sous-titrage pendant 5 secondes avant la coupure publicitaire à mi-parcours et pendant 5 secondes après la coupure publicitaire à mi-parcours.

>[!NOTE]
>
>Si un client demande qu’une vidéo soit lue dans une langue spécifique telle que l’anglais, puis demande de lire la vidéo en français, le serveur de manifeste ne peut pas détecter que le client a demandé de changer la langue en français. Le client ne communiquant pas avec le serveur de manifeste, le serveur de manifeste insère la légende publicitaire dans le flux vidéo en utilisant la première langue spécifiée dans le fichier maître M3U8 de l’annonce.
