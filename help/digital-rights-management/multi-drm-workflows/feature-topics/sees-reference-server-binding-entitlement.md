---
description: Le serveur de référence SEES vous montre comment activer le service de droits de liaison de périphérique à l'aide d'ExpressPlay.
seo-description: Le serveur de référence SEES vous montre comment activer le service de droits de liaison de périphérique à l'aide d'ExpressPlay.
seo-title: Droit de liaison de périphérique du service de référence
title: Droit de liaison de périphérique du service de référence
uuid: 22ce2f8e-1758-4528-8caf-60d209839afe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Service de référence : Droits de liaison de périphérique {#reference-service-device-binding-entitlement}

Le serveur de référence SEES vous montre comment activer le service de droits de liaison de périphérique à l&#39;aide d&#39;ExpressPlay.

>[!NOTE]
>
>Le service de droits liés au périphérique peut également être lié au temps ou fournir une durée de location.

Pour amorcer les `device_id` informations, lisez un contenu factice M3U8. Vous pouvez ensuite incorporer un cookie dans le jeton ExpressPlay, générer un SPC (qui contient le `device_id`) et envoyer un cookie `getToken` au serveur ExpressPlay.

![](assets/fees-device-binding.png)

La séquence début en jouant un factice M3U8. Un cookie est envoyé au serveur SEES pour obtenir l’URL du jeton ExpressPlay. Après avoir reçu l’URL du jeton ExpressPlay lié aux cookies, l’étape suivante consiste à générer le SPC et à l’envoyer au serveur ExpressPlay. Le serveur ExpressPlay extrait le cookie `device_id` à partir de SPC, le cookie à partir de l’URL du jeton ExpressPlay, puis le place dans le journal de transactions et le place `device_id` dans le cookie.

Le client envoie une vraie demande de licence à SEES en envoyant le même cookie. SEES utilise le cookie pour récupérer le fichier `device_id` à partir du serveur ExpressPlay.

SEES demande un jeton ExpressPlay lié au périphérique ainsi qu’au temps et renvoie ce jeton au client.

Le client effectue la demande de licence avec le jeton ExpressPlay.

Le serveur ExpressPlay compare le `device_id` SPC avec le `device_id` jeton ExpressPlay. Le serveur ExpressPlay émet une licence uniquement si les deux `device_id` valeurs correspondent.
