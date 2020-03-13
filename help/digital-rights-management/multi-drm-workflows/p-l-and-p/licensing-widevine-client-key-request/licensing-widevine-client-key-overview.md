---
description: Pour lire le contenu DASH résultant de l’assemblage du contenu, le client TVSDK doit obtenir la clé de déchiffrement du contenu transmise pendant le processus d’assemblage dans le processus d’acquisition de clés. La clé de déchiffrement du contenu client est généralement remise au client par un serveur de licence Widevine/PlayReady en réponse à une ou plusieurs publications HTTP/HTTPS du client.
seo-description: Pour lire le contenu DASH résultant de l’assemblage du contenu, le client TVSDK doit obtenir la clé de déchiffrement du contenu transmise pendant le processus d’assemblage dans le processus d’acquisition de clés. La clé de déchiffrement du contenu client est généralement remise au client par un serveur de licence Widevine/PlayReady en réponse à une ou plusieurs publications HTTP/HTTPS du client.
seo-title: Présentation du flux de travaux des demandes de clé client
title: Présentation du flux de travaux des demandes de clé client
uuid: 2f01f0ae-adbf-42fa-a908-4b5b9410a26d
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Processus de demande de clé client {#client-key-request-workflow-overview}

Pour lire le contenu DASH résultant de l’assemblage du contenu, le client TVSDK doit obtenir la clé de déchiffrement du contenu transmise pendant le processus d’assemblage dans le processus d’acquisition de clés. La clé de déchiffrement du contenu client est généralement remise au client par un serveur de licence Widevine/PlayReady en réponse à une ou plusieurs publications HTTP/HTTPS du client.

Pour acquérir la clé de déchiffrement du contenu, le client PSDK doit effectuer les opérations suivantes :

* Saisissez la zone de message du contenu, donnez-la à la plateforme et obtenez en réponse à une demande clé.
* Envoyez la demande de clé au serveur de licences Widevine/PlayReady approprié par le biais d’une requête HTTP POST.
* Transmettez la réponse du serveur à la plateforme qui extraira la clé de déchiffrement du contenu client de la réponse et l’utilisera pour le déchiffrement du contenu.

Pour envoyer le HTTP POST pour la demande de clé, votre code doit transmettre au client PSDK l’URL du serveur de licences, ainsi que toutes les données supplémentaires à joindre à la publication. Le choix de l’URL et des données à transmettre dépend du Widevine/PlayReady avec lequel vous travaillez. Par exemple, si vous utilisez ExpressPlay pour fournir le service, vous transmettez l’URL du serveur de licences ExpressPlay Widevine/PlayReady appropriée et vous joignez à la demande de clé sortante le jeton ExpressPlay associé à la clé de chiffrement du contenu. Vous pouvez obtenir l’URL appropriée du serveur de licences ExpressPlay Widevine/PlayReady à partir de la documentation ExpressPlay.