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

Utilisez la classe [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) pour mettre en oeuvre les interfaces de `ICCConfig`configuration, `IAAConfig``IPlaybackConfig`, `IAdConfig`et `IQosConfig` afin que les gestionnaires de fonctionnalités puissent lire les configurations. Par exemple, l’ `ICCConfig` interface est celle de la `CCManager` configuration. Les fichiers de configuration reçoivent les paramètres de configuration du fichier de configuration JSON.

Le `ConfigProvider.java` fichier est un exemple de l’implémentation des interfaces de configuration par Adobe. Il lit les paramètres de `SharedPreferences`l&#39;emplacement de stockage de la configuration. Vous pouvez stocker votre configuration de n’importe quelle manière compatible avec votre organisation. L’implémentation de la configuration fournit un wrapper pour votre source de configuration.