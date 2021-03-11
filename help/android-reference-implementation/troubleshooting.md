---
title: Dépannage
description: Dépannage
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 0%

---


# Dépannage{#troubleshooting}

* Pour certains périphériques plus anciens qui exécutent le niveau d&#39;API 10 ou plus, logcat ne peut pas ouvrir le périphérique de journal en raison d&#39;un problème d&#39;autorisation. L’exception suivante s’affiche : `java.lang.Exception: logcat returns error: Unable to open log device '/dev/log/main': Permission denied` **Solution :**

   1. Ouvrez [!DNL AndroidManifest.xml] sous le projet [!DNL CatalogActivity] dans l&#39;espace de travail.

   1. Ajoutez l&#39;autorisation suivante au fichier [!DNL `AndroidManfest.xml`] :

      ```
      android.permission.READ_LOGS
      ```
