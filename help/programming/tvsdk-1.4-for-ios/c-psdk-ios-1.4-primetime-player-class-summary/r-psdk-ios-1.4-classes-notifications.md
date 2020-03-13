---
description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certains   que le SDK TVSDK génère des problèmes à des fins de journalisation et de débogage.
seo-description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certains   que le SDK TVSDK génère des problèmes à des fins de journalisation et de débogage.
seo-title: Classes de notification
title: Classes de notification
uuid: 08c29efe-245d-4a6d-80c6-cd561cbf3b5f
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Classes de notification{#notification-classes}

Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certains   que le SDK TVSDK génère des problèmes à des fins de journalisation et de débogage.

| Nom de la classe | Description |
|---|---|
| [PTMediaError](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaError.html) | Classe qui décrit la notification en cas d’erreur entraînant l’arrêt de la lecture du lecteur. Il s’agit d’une [notification PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) du type de notification ERROR. |
| [PTMediaPlayerNotifications](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerNotifications.html) | toutes les notifications envoyées par la structure du lecteur Primetime. |
| [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) | Classe qui fournit des messages d’informations, des avertissements et des erreurs. Encapsule la représentation d’objet d’un de notification unique dans [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html). |
| [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) | Classe qui stocke un journal des objets de notification [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) qui permet d’accéder à un d’historique de  de notification un . En d’autres termes, il conserve un  d’éléments, chaque élément contenant une instance distincte de [PTNotification.](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) |
| [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) | Classe qui définit une entrée dans le circulaire dans [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) et qui contient la notification et son horodatage. |

