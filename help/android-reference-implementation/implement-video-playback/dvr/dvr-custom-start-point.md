---
description: Vous pouvez choisir un point de départ personnalisé pour le moment où entrer un flux de l’enregistrement numérique (DVR) plutôt que le comportement par défaut de saisir le flux de l’enregistrement numérique au début à l’aide de la classe ConfigProvider .
title: Choix d’un point de départ personnalisé pour la conservation des données
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Choix d’un point de départ personnalisé pour la conservation des données {#choosing-a-custom-starting-point-for-dvr}

Vous pouvez choisir un point de départ personnalisé pour le moment où entrer un flux de l’enregistrement numérique (DVR) plutôt que le comportement par défaut de saisir le flux de l’enregistrement numérique au début à l’aide de la classe ConfigProvider .

Pour définir l’heure de début via la variable [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) Classe :

1. Activer [isCustomPositionPrefEnabled()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html#isCustomPositionPrefEnabled()).
1. Définissez l’heure de début dans [retrieveStartTimePref()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#iretrieveStartTimePref()).
1. Vérifiez que la position de départ personnalisée est activée.
