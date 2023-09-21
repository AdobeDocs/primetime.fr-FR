---
description: Pour lire le contenu DASH résultant du package de contenu, le client TVSDK doit obtenir la clé de déchiffrement de contenu qui a été transmise pendant le processus de conditionnement dans le workflow d’acquisition de clé. La clé de décryptage du contenu client est généralement fournie au client par un serveur de licence Widevine/PlayReady en réponse à une ou plusieurs publications HTTP/HTTPS du client.
title: Workflow de demande de clé client - Aperçu
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Workflow de demande de clé client {#client-key-request-workflow-overview}

Pour lire le contenu DASH résultant du package de contenu, le client TVSDK doit obtenir la clé de déchiffrement de contenu qui a été transmise pendant le processus de conditionnement dans le workflow d’acquisition de clé. La clé de décryptage du contenu client est généralement fournie au client par un serveur de licence Widevine/PlayReady en réponse à une ou plusieurs publications HTTP/HTTPS du client.

Pour acquérir la clé de décryptage du contenu, le client PSDK doit procéder comme suit :

* Saisissez la boîte push du contenu, donnez-la à la plateforme et obtenez en réponse à une requête clé.
* Envoyez la demande de clé au serveur de licence Widevine/PlayReady approprié via un POST HTTP.
* Transmettez la réponse du serveur à la plateforme qui extraira la clé de déchiffrement du contenu client de la réponse et l’utilisera pour le déchiffrement du contenu.

Pour envoyer le POST HTTP pour la demande de clé, votre code doit transmettre au client PSDK l’URL du serveur de licences avec toutes les données supplémentaires qui doivent être jointes à la publication. Le choix de l’URL et des données à transmettre dépend du fournisseur de services Widevine/PlayReady avec lequel vous travaillez. Par exemple, si vous utilisez ExpressPlay pour fournir le service, vous transmettez l’URL du serveur de licences ExpressPlay Windows/PlayReady appropriée et joignez à la demande de clé sortante le jeton ExpressPlay associé à la clé de chiffrement du contenu. Vous pouvez obtenir l’URL appropriée du serveur de licences ExpressPlay Windows/PlayReady à partir de la documentation ExpressPlay.
