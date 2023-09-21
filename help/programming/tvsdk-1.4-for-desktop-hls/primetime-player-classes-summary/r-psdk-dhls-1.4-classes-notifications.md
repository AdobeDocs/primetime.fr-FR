---
description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités qui posent problème à des fins de journalisation et de débogage.
title: Classes de notification
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Classes de notification {#notification-classes}

Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités qui posent problème à des fins de journalisation et de débogage.

Package : [com.adobe.mediacore.notifications](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/package-detail.html)

| Nom de la classe | Description |
|---|---|
| [Notification](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) | Classe fournissant des informations sur les messages, les avertissements et les erreurs. Encapsule la représentation d’objet d’un événement de notification unique dans [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html). |
| [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationCode.html) | Renvoie la description associée au code de notification fourni et fournit des constantes numériques pour les objets de notification. |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) | Classe qui stocke un journal des objets de notification. Une liste circulaire de [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) qui permet d’accéder à une liste de l’historique des événements de notification. En d’autres termes, il conserve une liste d’éléments, chaque élément contenant une instance séparée de la variable [Notification](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/Notification.html) classe . |
| [NotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistoryItem.html) | Classe qui définit une entrée dans la liste circulaire dans [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationHistory.html) et contient la notification et son horodatage. |
| [NotificationType](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/notifications/NotificationType.html) | Classe contenant les types de notifications pris en charge. |
