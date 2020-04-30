---
description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités qui posent problème pour la journalisation et le débogage.
seo-description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités qui posent problème pour la journalisation et le débogage.
seo-title: Classes de notification
title: Classes de notification
uuid: 3befc64b-4abd-47df-9c45-215b49029757
translation-type: tm+mt
source-git-commit: ''

---


# Classes de notification {#notification-classes}

Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités qui posent problème pour la journalisation et le débogage.

Package : [com.adobe.mediacore.notifications](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/package-detail.html)

| Nom de la classe | Description |
|---|---|
| [Notification](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) | Classe qui fournit des messages d’informations, des avertissements et des erreurs. Encapsule la représentation d&#39;objet d&#39;un seul événement de notification dans [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html). |
| [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationCode.html) | Renvoie la description associée au code de notification fourni et fournit des constantes numériques pour les objets de notification. |
| [Historique des notifications](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) | Classe qui stocke un journal des objets de notification. liste circulaire d&#39;objets [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) qui permet d&#39;accéder à une liste d&#39;historique des événements de notification. En d&#39;autres termes, il conserve une liste d&#39;éléments, chaque élément contenant une instance distincte de la classe [Notification](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) . |
| [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) | Classe qui définit une entrée dans la liste circulaire dans [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) et contient la notification et son horodatage. |
| [NotificationType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationType.html) | Classe contenant les types de notifications pris en charge. |

