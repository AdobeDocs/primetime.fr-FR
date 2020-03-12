---
description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certains   que le SDK TVSDK génère des problèmes à des fins de journalisation et de débogage.
seo-description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certains   que le SDK TVSDK génère des problèmes à des fins de journalisation et de débogage.
seo-title: Classes de notification
title: Classes de notification
uuid: e231a2d0-6190-4251-87db-ca46d2aee60d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Classes de notification{#notification-classes}

Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certains   que le SDK TVSDK génère des problèmes à des fins de journalisation et de débogage.

Package : Package [com.adobe.mediacore](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/package-summary.html) : [com.adobe.mediacore.session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html)

| Nom de la classe | Description |
|---|---|
| MediaPlayerNotification. [Erreur](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Error.html) | Classe qui décrit la notification en cas d’erreur entraînant l’arrêt de la lecture du lecteur. Il s’agit d’une notification [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) de type de notification ERROR. |
| MediaPlayerNotification. [Infos](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Info.html) | Classe qui décrit une notification d’informations. Il s’agit d’un [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) de type de notification INFO. |
| MediaPlayerNotification. [Avertissement](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) | Classe décrivant une notification d’avertissement. Il s’agit d’un [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) de type de notification WARNING. |
| [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) | Classe qui fournit des messages d’informations, des avertissements et des erreurs. Encapsule la représentation d’objet d’un de notification unique dans [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html). |
| MediaPlayerNotification. [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.NotificationCode.html) | Renvoie la description associée au code de notification fourni. |
| [Historique des notifications](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) | Classe qui stocke un journal des objets de notification. circulaire d’objets [NotificationHistory.Item](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) qui permet d’accéder à un  d’historique de de notification  un . En d’autres termes, il conserve un  d’éléments, chaque élément contenant une instance distincte de la classe [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) . (Dans le package de [session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html) .) |
| NotificationHistory. [Elément](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) | Classe qui définit une entrée dans le circulaire dans [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) et qui contient la notification et son horodatage. |
| MediaPlayerNotification. [EntryType](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.EntryType.html) | Classe contenant les types de notifications pris en charge. |