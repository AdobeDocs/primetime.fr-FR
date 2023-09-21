---
description: La classe ConfigProvider obtient la configuration pour le lecteur multimédia. Vous devez mettre en oeuvre l’interface de configuration afin que les gestionnaires de fonctionnalités puissent lire les informations de configuration.
title: ConfigProvider
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# ConfigProvider {#configprovider}

La classe ConfigProvider obtient la configuration pour le lecteur multimédia. Vous devez mettre en oeuvre l’interface de configuration afin que les gestionnaires de fonctionnalités puissent lire les informations de configuration.

Vous utilisez la variable [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) pour mettre en oeuvre la classe `ICCConfig`, `IAAConfig`, `IPlaybackConfig`, `IAdConfig`, et `IQosConfig` des interfaces de configuration afin que les gestionnaires de fonctionnalités puissent lire les configurations. Par exemple, la variable `ICCConfig` est l’interface de la fonction `CCManager` configuration. Les fichiers de configuration reçoivent les paramètres de configuration du fichier de configuration JSON.

La variable `ConfigProvider.java` est un exemple d’implémentation des interfaces de configuration par Adobe. Il lit les paramètres depuis `SharedPreferences`, où la configuration est stockée. Vous pouvez stocker votre configuration de n’importe quelle manière qui fonctionne pour votre organisation. La mise en oeuvre de la configuration fournit un wrapper pour votre source de configuration.
