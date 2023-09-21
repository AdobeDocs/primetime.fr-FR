---
title: Dépannage
description: Dépannage
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 0%

---

# Dépannage{#troubleshooting}

* Pour certains appareils plus anciens qui exécutent une API de niveau 10 ou plus, logcat ne peut pas ouvrir l’appareil de journal en raison d’un problème d’autorisation. L’exception suivante s’affiche : `java.lang.Exception: logcat returns error: Unable to open log device '/dev/log/main': Permission denied` **Solution :**

   1. Ouvrir [!DNL AndroidManifest.xml] sous le [!DNL CatalogActivity] dans l’espace de travail.

   1. Ajoutez l’autorisation suivante au [!DNL `AndroidManfest.xml`] fichier :

      ```
      android.permission.READ_LOGS
      ```
