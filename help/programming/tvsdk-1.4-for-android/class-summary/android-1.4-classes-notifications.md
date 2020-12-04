---
description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités que TVSDK génère à des fins de journalisation et de débogage.
seo-description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités que TVSDK génère à des fins de journalisation et de débogage.
seo-title: Classes de notification
title: Classes de notification
uuid: e231a2d0-6190-4251-87db-ca46d2aee60d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---


# Classes de notification{#notification-classes}

Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités que TVSDK génère à des fins de journalisation et de débogage.

Package : [com.adobe.mediacore](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/package-summary.html) Package : [com.adobe.mediacore.session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html)

| Nom de la classe | Description |
|---|---|
| MediaPlayerNotification. [Erreur](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Error.html) | Classe qui décrit la notification d’une erreur qui entraîne l’arrêt de la lecture du lecteur. Il s&#39;agit d&#39;un [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) de type de notification ERROR. |
| MediaPlayerNotification. [Infos](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Info.html) | Classe qui décrit une notification d&#39;informations. Il s&#39;agit d&#39;un [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) de type de notification INFO. |
| MediaPlayerNotification. [Avertissement](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) | Classe qui décrit une notification d&#39;avertissement. Il s&#39;agit d&#39;un [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) de type de notification AVERTISSEMENT. |
| [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) | Classe qui fournit des messages d’informations, des avertissements et des erreurs. Encapsule la représentation d&#39;objet d&#39;un événement de notification unique dans [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html). |
| MediaPlayerNotification. [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.NotificationCode.html) | Renvoie la description associée au code de notification fourni. |
| [Historique des notifications](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) | Classe qui stocke un journal des objets de notification. Liste circulaire d&#39;objets [NotificationHistory.Item](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) qui permet d&#39;accéder à une liste d&#39;historique des événements de notification. En d’autres termes, il conserve une liste d’éléments, chaque élément contenant une instance distincte de la classe [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html). (Dans le package [session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html).) |
| NotificationHistory. [Elément](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) | Classe qui définit une entrée dans la liste circulaire de [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) et contient la notification et son horodatage. |
| MediaPlayerNotification. [EntryType](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.EntryType.html) | Classe contenant les types de notifications pris en charge. |