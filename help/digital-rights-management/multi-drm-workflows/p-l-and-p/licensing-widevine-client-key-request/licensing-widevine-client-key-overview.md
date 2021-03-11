---
description: Pour lire le contenu DASH résultant de l’assemblage du contenu, le client TVSDK doit obtenir la clé de déchiffrement du contenu transmise pendant le processus d’assemblage dans le processus d’acquisition de clés. La clé de déchiffrement du contenu client est généralement remise au client par un serveur de licence Widevine/PlayReady en réponse à une ou plusieurs publications HTTP/HTTPS du client.
title: Présentation du processus de demande de clé client
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---


# Processus de demande de clé client {#client-key-request-workflow-overview}

Pour lire le contenu DASH résultant de l’assemblage du contenu, le client TVSDK doit obtenir la clé de déchiffrement du contenu transmise pendant le processus d’assemblage dans le processus d’acquisition de clés. La clé de déchiffrement du contenu client est généralement remise au client par un serveur de licence Widevine/PlayReady en réponse à une ou plusieurs publications HTTP/HTTPS du client.

Pour obtenir la clé de déchiffrement du contenu, le client PSDK doit effectuer les opérations suivantes :

* Saisissez la zone de message du contenu, donnez-la à la plate-forme et obtenez-la en réponse à une demande de clé.
* Envoyez la demande de clé au serveur de licences Widevine/PlayReady approprié par l’intermédiaire d’un POST HTTP.
* Transmettez la réponse du serveur à la plateforme qui extraira la clé de déchiffrement du contenu client de la réponse et l’utilisera pour le déchiffrement du contenu.

Pour envoyer le POST HTTP pour la demande de clé, votre code doit transmettre au client PSDK l’URL du serveur de licences ainsi que toute donnée supplémentaire à joindre à la publication. Le choix de l&#39;URL et des données à transmettre dépend du prestataire Widevine/PlayReady avec lequel vous travaillez. Par exemple, si vous utilisez ExpressPlay pour fournir le service, vous transmettez l’URL du serveur de licences ExpressPlay Widevine/PlayReady appropriée et vous joignez à la demande de clé sortante le jeton ExpressPlay associé à la clé de chiffrement du contenu. Vous pouvez obtenir l’URL appropriée du serveur de licences ExpressPlay Widevine/PlayReady à partir de la documentation ExpressPlay.