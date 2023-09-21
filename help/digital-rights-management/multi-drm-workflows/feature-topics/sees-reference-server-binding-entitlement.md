---
description: Le serveur de référence SEES vous indique comment activer le service de droits de liaison d’appareil à l’aide d’ExpressPlay.
title: Droit de liaison d’appareil du service de référence
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Service de référence : droit de liaison d’appareil {#reference-service-device-binding-entitlement}

Le serveur de référence SEES vous indique comment activer le service de droits de liaison d’appareil à l’aide d’ExpressPlay.

>[!NOTE]
>
>Le service de droits lié aux appareils peut également être lié au temps ou fournir une durée de location.

Pour démarrer la fonction `device_id` informations, lecture d’un contenu factice M3U8. Vous pouvez ensuite incorporer un cookie dans le jeton ExpressPlay et générer un SPC (qui contient le `device_id`), puis envoyer un `getToken` au serveur ExpressPlay.

![](assets/fees-device-binding.png)

La séquence commence par la lecture d’un factice M3U8. Un cookie est envoyé au serveur SEES pour obtenir l’URL du jeton ExpressPlay. Après avoir reçu l’URL du jeton ExpressPlay lié aux cookies, l’étape suivante consiste à générer le SPC et à l’envoyer au serveur ExpressPlay. Le serveur ExpressPlay extrait la variable `device_id` à partir de SPC, le cookie de l’URL du jeton ExpressPlay, et place le cookie et `device_id` dans le journal des transactions.

Le client émet une demande de licence réelle pour que SEES envoie le même cookie. SEES utilise le cookie pour récupérer la variable `device_id` à partir du serveur ExpressPlay.

SEES demande un jeton ExpressPlay lié à l’appareil, ainsi qu’un jeton temporel, et renvoie ce jeton au client.

Le client effectue la demande de licence avec le jeton ExpressPlay.

Le serveur ExpressPlay compare la variable `device_id` dans le SPC avec la fonction `device_id` dans le jeton ExpressPlay. Le serveur ExpressPlay émet une licence uniquement si les deux `device_id` correspondent.
