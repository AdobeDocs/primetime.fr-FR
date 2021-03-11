---
description: La classe ConfigProvider obtient la configuration du lecteur de médias. Vous devez mettre en oeuvre l’interface de configuration pour que les gestionnaires de fonctionnalités puissent lire les informations de configuration.
title: ConfigProvider
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---


# ConfigProvider {#configprovider}

La classe ConfigProvider obtient la configuration du lecteur de médias. Vous devez mettre en oeuvre l’interface de configuration pour que les gestionnaires de fonctionnalités puissent lire les informations de configuration.

Utilisez la classe [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) pour implémenter les interfaces de configuration `ICCConfig`, `IAAConfig`, `IPlaybackConfig`, `IAdConfig` et `IQosConfig` afin que les gestionnaires de fonctionnalités puissent lire les configurations. Par exemple, `ICCConfig` est l&#39;interface de la configuration `CCManager`. Les fichiers de configuration reçoivent les paramètres de configuration du fichier de configuration JSON.

Le fichier `ConfigProvider.java` est un exemple d&#39;implémentation par Adobe des interfaces de configuration. Il lit les paramètres de `SharedPreferences`, où la configuration est stockée. Vous pouvez stocker votre configuration de n’importe quelle manière compatible avec votre organisation. L’implémentation de la configuration fournit un wrapper pour votre source de configuration.