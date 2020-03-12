---
description: Les gestionnaires de fonctionnalités sont des wrappers autour de la bibliothèque TVSDK.
seo-description: Les gestionnaires de fonctionnalités sont des wrappers autour de la bibliothèque TVSDK.
seo-title: Structure d’implémentation de référence
title: Structure d’implémentation de référence
uuid: ae347a97-1500-476a-9fc8-c99e6b2ab8de
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Structure d’implémentation de référence {#reference-implementation-structure}

Les gestionnaires de fonctionnalités sont des wrappers autour de la bibliothèque TVSDK.

Dans Java, les classes sont structurées dans une hiérarchie. Par exemple, tout le code lié à l’interface utilisateur sous `com.adobe.primetime.reference.ui` et tous les gestionnaires de fonctionnalités sont sous `com.adobe.primetime.reference.manager`.

L’implémentation de référence Primetime contient les packages suivants :

| Package | Description |
|--- |--- |
| [com.adobe.primetime.reference](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/PrimetimeReference.html) | Cette classe étend android.app.Application. |
| [com.adobe.primetime.reference.publicitaire](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/advertising/package-summary.html) | Contient le code des annonces personnalisées. |
| [com.adobe.primetime.reference.config](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html) | Contient le code d’interface requis pour configurer les gestionnaires de fonctionnalités. |
| [com.adobe.primetime.reference.drm](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/drm/package-summary.html) | Contient des classes d’aide pour DRM. |
| [com.adobe.primetime.reference.feeds](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/feeds/package-summary.html) | Les adaptateurs et les adaptateurs d’élément pour l’interface, la plate-forme et les informations de référence. Inclut également le code FeedAdapterFactory, ContentRenditionInfo et XMLParserHelper. |
| [com.adobe.primetime.reference.logging](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/logging/package-summary.html) | Fournit des classes pour la connexion locale et distante. |
| [com.adobe.primetime.reference.manager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/package-summary.html) | C&#39;est là que vous trouverez les gestionnaires de fonctionnalités ainsi que le gestionnaireFactory. Pour les fonctionnalités facultatives que vous pouvez activer ou désactiver, il existe deux gestionnaires de fonctionnalités : <ul><li>Un gestionnaire de fonctionnalités est le nom de la fonctionnalité, par exemple, CCManager. Ce gestionnaire de fonctionnalités est désactivé et fournit le comportement de désactivation par défaut.</li><li>Un gestionnaire de fonctionnalités auquel l’option Activé est ajoutée au nom du gestionnaire de fonctionnalités, par exemple, CCManagerOn. Ce gestionnaire de fonctionnalités fournit un exemple de code pour la fonction activée.</li></ul> |
| [com.adobe.primetime.reference.ui.catalog](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/catalog/package-summary.html) | Contient le code d’interface utilisateur du catalogue. |
| [com.adobe.primetime.reference.ui.log](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/log/package-summary.html) | Contient le code de l’interface utilisateur pour le journal. |
| [com.adobe.primetime.reference.ui.player](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/package-summary.html) | Contient le code d’interface utilisateur du lecteur. |
| [com.adobe.primetime.reference.ui.seésentation](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/settings/package-summary.html) | Contient le code d’interface utilisateur des paramètres. |
| [com.adobe.primetime.reference.utils](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/utils/package-summary.html) | Contient des classes d’utilitaires générales. |
| [com.adobe.primetime.reference.utils.http](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/utils/http/package-summary.html) | Contient des classes `HTTP-specific` d’utilitaires. |
