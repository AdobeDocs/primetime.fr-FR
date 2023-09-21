---
description: Les gestionnaires de fonctionnalités servent d’encapsulation autour de la bibliothèque TVSDK.
title: Structure de l’implémentation de référence
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Structure de l’implémentation de référence {#reference-implementation-structure}

Les gestionnaires de fonctionnalités servent d’encapsulation autour de la bibliothèque TVSDK.

Dans Java, les classes sont structurées dans une hiérarchie. Par exemple, tout le code lié à l’interface utilisateur sous `com.adobe.primetime.reference.ui` et tous les gestionnaires de fonctionnalités sont sous `com.adobe.primetime.reference.manager`.

L’implémentation de référence Primetime contient les packages suivants :

| Package | Description |
|--- |--- |
| [com.adobe.primetime.reference](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/PrimetimeReference.html) | Cette classe étend android.app.Application. |
| [com.adobe.primetime.reference.advertising](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/advertising/package-summary.html) | Contient du code pour les publicités personnalisées. |
| [com.adobe.primetime.reference.config](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html) | Contient le code d’interface requis pour la configuration des gestionnaires de fonctionnalités. |
| [com.adobe.primetime.reference.drm](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/drm/package-summary.html) | Contient des classes d’assistance pour DRM. |
| [com.adobe.primetime.reference.feeds](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/feeds/package-summary.html) | Les adaptateurs et les adaptateurs d’élément pour les informations d’interface, de plateforme et de référence. Comprend également le code FeedAdapterFactory, ContentRenditionInfo et XMLParserHelper. |
| [com.adobe.primetime.reference.logging](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/logging/package-summary.html) | Fournit des classes pour la journalisation locale et distante. |
| [com.adobe.primetime.reference.manager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/package-summary.html) | C’est là que vous pouvez trouver les gestionnaires de fonctionnalités ainsi que ManagerFactory. Pour les fonctionnalités facultatives que vous pouvez activer ou désactiver, il existe deux gestionnaires de fonctionnalités : <ul><li>Un gestionnaire de fonctionnalités qui est le nom de la fonctionnalité, par exemple, CCManager. Ce gestionnaire de fonctionnalités est désactivé et fournit le comportement de désactivation par défaut.</li><li>Un gestionnaire de fonctionnalités auquel l’opérateur On est ajouté au nom du gestionnaire de fonctionnalités, par exemple, CCManagerOn. Ce gestionnaire de fonctionnalités fournit un exemple de code pour la fonctionnalité activée.</li></ul> |
| [com.adobe.primetime.reference.ui.catalent](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/catalog/package-summary.html) | Contient le code d’interface utilisateur du catalogue. |
| [com.adobe.primetime.reference.ui.log](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/log/package-summary.html) | Contient le code d’interface utilisateur du journal. |
| [com.adobe.primetime.reference.ui.player](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/package-summary.html) | Contient le code d’interface utilisateur du lecteur. |
| [com.adobe.primetime.reference.ui.settings](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/settings/package-summary.html) | Contient le code d’interface utilisateur des paramètres. |
| [com.adobe.primetime.reference.utils](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/utils/package-summary.html) | Contient des classes d’utilitaires générales. |
| [com.adobe.primetime.reference.utils.http](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/utils/http/package-summary.html) | Contient `HTTP-specific` classes d’utilitaires. |
