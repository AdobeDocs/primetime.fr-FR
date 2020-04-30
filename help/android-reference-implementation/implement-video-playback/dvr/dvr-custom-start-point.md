---
description: Vous pouvez choisir un point de départ personnalisé pour le moment où entrer un flux DVR au lieu du comportement par défaut de la saisie du flux DVR au début à l'aide de la classe ConfigProvider.
seo-description: Vous pouvez choisir un point de départ personnalisé pour le moment où entrer un flux DVR au lieu du comportement par défaut de la saisie du flux DVR au début à l'aide de la classe ConfigProvider.
seo-title: Choix d’un point de départ personnalisé pour la magnétoscopie numérique
title: Choix d’un point de départ personnalisé pour la magnétoscopie numérique
uuid: a7e13865-2b86-4234-ac4c-9a5320b293db
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Choix d’un point de départ personnalisé pour la magnétoscopie numérique {#choosing-a-custom-starting-point-for-dvr}

Vous pouvez choisir un point de départ personnalisé pour le moment où entrer un flux DVR au lieu du comportement par défaut de la saisie du flux DVR au début à l&#39;aide de la classe ConfigProvider.

Pour définir l&#39;heure de début par l&#39;intermédiaire de la classe [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) :

1. Activez [isCustomPositionPrefEnabled()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html#isCustomPositionPrefEnabled()).
1. Définissez l’heure de début dans [retrieveStartTimePref()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#iretrieveStartTimePref()).
1. Vérifiez que la position du début personnalisé est activée.
