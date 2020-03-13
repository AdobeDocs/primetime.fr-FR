---
description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certains   les problèmes de journalisation et de débogage.
seo-description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certains   les problèmes de journalisation et de débogage.
seo-title: Classes de notification
title: Classes de notification
uuid: 3befc64b-4abd-47df-9c45-215b49029757
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Classes de notification {#notification-classes}

Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certains   les problèmes de journalisation et de débogage.

Package : [com.adobe.mediacore.notifications](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/package-detail.html)

| Nom de la classe | Description |
|---|---|
| [Notification](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) | Classe qui fournit des messages d’informations, des avertissements et des erreurs. Encapsule la représentation d’objet d’un de notification unique dans [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html). |
| [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationCode.html) | Renvoie la description associée au code de notification fourni et fournit des constantes numériques pour les objets de notification. |
| [Historique des notifications](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) | Classe qui stocke un journal des objets de notification. circulaire d’objets [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) qui permet d’accéder à un  d’historique de l’de notification  un . En d’autres termes, il conserve un d’éléments, chaque élément contenant une instance distincte de la classe [Notification](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) . |
| [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) | Classe qui définit une entrée dans le circulaire dans [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) et qui contient la notification et son horodatage. |
| [NotificationType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationType.html) | Classe contenant les types de notifications pris en charge. |

