---
description: Le serveur de référence SEES vous montre comment activer le service de droits de liaison de périphérique à l'aide d'ExpressPlay.
title: Droit de liaison de périphérique du service de référence
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# Service de référence : Droit de liaison de périphérique {#reference-service-device-binding-entitlement}

Le serveur de référence SEES vous montre comment activer le service de droits de liaison de périphérique à l&#39;aide d&#39;ExpressPlay.

>[!NOTE]
>
>Le service de droits liés au périphérique peut également être lié au temps ou fournir une durée de location.

Pour amorcer les informations `device_id`, lisez un contenu factice M3U8. Vous pouvez ensuite incorporer un cookie dans le jeton ExpressPlay, générer un SPC (qui contient `device_id`) et envoyer un `getToken` au serveur ExpressPlay.

![](assets/fees-device-binding.png)

La séquence début en jouant un factice M3U8. Un cookie est envoyé au serveur SEES pour obtenir l’URL du jeton ExpressPlay. Après avoir reçu l’URL du jeton ExpressPlay lié aux cookies, l’étape suivante consiste à générer le SPC et à l’envoyer au serveur ExpressPlay. Le serveur ExpressPlay extrait le `device_id` de SPC, le cookie de l’URL du jeton ExpressPlay, et place le cookie et `device_id` dans le journal de transactions.

Le client envoie une vraie demande de licence à SEES en envoyant le même cookie. SEES utilise le cookie pour récupérer `device_id` du serveur ExpressPlay.

SEES demande un jeton ExpressPlay lié au périphérique ainsi qu’au temps et renvoie ce jeton au client.

Le client effectue la demande de licence avec le jeton ExpressPlay.

Le serveur ExpressPlay compare le `device_id` du SPC avec le `device_id` du jeton ExpressPlay. Le serveur ExpressPlay émet une licence uniquement si les deux valeurs `device_id` correspondent.
