---
description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités que TVSDK génère à des fins de journalisation et de débogage.
seo-description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités que TVSDK génère à des fins de journalisation et de débogage.
seo-title: Classes de notification
title: Classes de notification
uuid: 8a276056-775f-432d-a4b4-722f6e4e278f
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---


# Classes de notification {#notification-classes}

Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités que TVSDK génère à des fins de journalisation et de débogage.

| **Nom de la classe** | **Description** |
|---|---|
| [PTMediaError](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaError.html) | Classe qui décrit la notification d’une erreur qui entraîne l’arrêt de la lecture du lecteur. Il s&#39;agit d&#39;un [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) du type de notification ERROR. |
| [PTMediaPlayerNotifications](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerNotifications.html) | Liste toutes les notifications envoyées par la structure du lecteur Primetime. |
| [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) | Classe qui fournit des messages d’informations, des avertissements et des erreurs. Encapsule la représentation d&#39;objet d&#39;un événement de notification unique dans [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html). |
| [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) | Classe qui stocke un journal des objets de notification [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) qui permet d&#39;accéder à une liste d&#39;historique des événements de notification. En d’autres termes, il conserve une liste d’éléments, chaque élément contenant une instance distincte de [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html). |
| [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) | Classe qui définit une entrée dans la liste circulaire de [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) et qui contient la notification et son horodatage. |

