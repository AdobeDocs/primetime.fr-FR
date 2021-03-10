---
description: Vous pouvez choisir un point de départ personnalisé pour le moment où entrer un flux DVR au lieu du comportement par défaut de la saisie du flux DVR au début à l'aide de la classe ConfigProvider.
title: Choix d’un point de départ personnalisé pour la magnétoscopie numérique
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# Choix d’un point de départ personnalisé pour le rapport DVR {#choosing-a-custom-starting-point-for-dvr}

Vous pouvez choisir un point de départ personnalisé pour le moment où entrer un flux DVR au lieu du comportement par défaut de la saisie du flux DVR au début à l&#39;aide de la classe ConfigProvider.

Pour définir l&#39;heure de début par l&#39;intermédiaire de la classe [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) :

1. Activez [isCustomPositionPrefEnabled()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html#isCustomPositionPrefEnabled()).
1. Définissez l’heure de début dans [retrieveStartTimePref()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#iretrieveStartTimePref()).
1. Vérifiez que la position du début personnalisé est activée.
