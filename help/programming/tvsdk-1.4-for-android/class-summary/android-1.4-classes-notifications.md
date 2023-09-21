---
description: Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités que TVSDK génère à des fins de journalisation et de débogage.
title: Classes de notification
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Classes de notification{#notification-classes}

Ces classes décrivent les messages relatifs aux erreurs, aux avertissements et à certaines activités que TVSDK génère à des fins de journalisation et de débogage.

Package : [com.adobe.mediacore](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/package-summary.html)  Package : [com.adobe.mediacore.session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html)

| Nom de la classe | Description |
|---|---|
| MediaPlayerNotification. [Erreur](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Error.html) | Classe qui décrit la notification d’une erreur qui entraîne l’arrêt de la lecture du lecteur. Ceci est une [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) de type de notification ERROR. |
| MediaPlayerNotification. [Infos](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Info.html) | Classe qui décrit une notification d’informations. Ceci est une [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) de type notification INFO. |
| MediaPlayerNotification. [Avertissement](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) | Classe décrivant une notification d’avertissement. Ceci est une [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) de type de notification AVERTISSEMENT. |
| [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) | Classe fournissant des informations sur les messages, les avertissements et les erreurs. Encapsule la représentation d’objet d’un événement de notification unique dans [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html). |
| MediaPlayerNotification. [NotificationCode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.NotificationCode.html) | Renvoie la description associée au code de notification fourni. |
| [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) | Classe qui stocke un journal des objets de notification. Une liste circulaire de [NotificationHistory.Item](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) qui permet d’accéder à une liste de l’historique des événements de notification. En d’autres termes, il conserve une liste d’éléments, chaque élément contenant une instance séparée de la variable [MediaPlayerNotification](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html) classe . (Dans [session](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/package-summary.html) module .) |
| NotificationHistory [Élément](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.Item.html) | Classe qui définit une entrée dans la liste circulaire dans [NotificationHistory](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/session/NotificationHistory.html) et contient la notification et son horodatage. |
| MediaPlayerNotification. [EntryType](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.EntryType.html) | Classe contenant les types de notifications pris en charge. |
