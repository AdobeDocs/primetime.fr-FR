---
description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités que TVSDK génère à des fins de journalisation et de débogage.
title: Classes de notification
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Classes de notification{#notification-classes}

Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités que TVSDK génère à des fins de journalisation et de débogage.

| Nom de la classe | Description |
|---|---|
| [PTMediaError](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaError.html) | Classe qui décrit la notification d’une erreur qui entraîne l’arrêt de la lecture du lecteur. Ceci est une [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) de type de notification ERROR. |
| [PTMediaPlayerNotifications](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerNotifications.html) | Répertorie toutes les notifications distribuées par la structure du lecteur Primetime. |
| [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) | Classe fournissant des informations sur les messages, les avertissements et les erreurs. Encapsule la représentation d’objet d’un événement de notification unique dans [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html). |
| [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) | Classe qui stocke un journal des objets de notification [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) qui permet d’accéder à une liste de l’historique des événements de notification. En d’autres termes, il conserve une liste d’éléments, chaque élément contenant une instance séparée de la variable [PTNotification](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotification.html) |
| [PTNotificationHistoryItem](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistoryItem.html) | Classe qui définit une entrée dans la liste circulaire dans [PTNotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTNotificationHistory.html) et contient la notification et son horodatage. |
