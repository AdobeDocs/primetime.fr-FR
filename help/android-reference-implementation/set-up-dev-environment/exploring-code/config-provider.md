---
description: La classe ConfigProvider obtient la configuration du lecteur de médias. Vous devez mettre en oeuvre l’interface de configuration pour que les gestionnaires de fonctionnalités puissent lire les informations de configuration.
seo-description: La classe ConfigProvider obtient la configuration du lecteur de médias. Vous devez mettre en oeuvre l’interface de configuration pour que les gestionnaires de fonctionnalités puissent lire les informations de configuration.
seo-title: ConfigProvider
title: ConfigProvider
uuid: 2467a617-6413-4b5d-9710-894cdc751b26
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# ConfigProvider {#configprovider}

La classe ConfigProvider obtient la configuration du lecteur de médias. Vous devez mettre en oeuvre l’interface de configuration pour que les gestionnaires de fonctionnalités puissent lire les informations de configuration.

Utilisez la classe [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) pour implémenter les interfaces `ICCConfig`, `IAAConfig`, `IPlaybackConfig`, `IAdConfig`et `IQosConfig` de configuration afin que les gestionnaires de fonctionnalités puissent lire les configurations. Par exemple, `ICCConfig` est l’interface de la `CCManager` configuration. Les fichiers de configuration reçoivent les paramètres de configuration du fichier de configuration JSON.

Le `ConfigProvider.java` fichier est un exemple de l’implémentation par Adobe des interfaces de configuration. Il lit les paramètres `SharedPreferences`, d&#39;où la configuration est stockée. Vous pouvez stocker votre configuration de n’importe quelle manière qui fonctionne pour votre entreprise. L’implémentation de configuration fournit un wrapper pour votre source de configuration.