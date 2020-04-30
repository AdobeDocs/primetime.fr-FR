---
seo-title: Dépannage
title: Dépannage
uuid: b7a41ea7-86c5-442c-b751-86a9055c5e35
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Dépannage{#troubleshooting}

* Pour certains périphériques plus anciens qui exécutent le niveau d&#39;API 10 ou plus, logcat ne peut pas ouvrir le périphérique de journal en raison d&#39;un problème d&#39;autorisation. L’exception suivante s’affiche : `java.lang.Exception: logcat returns error: Unable to open log device '/dev/log/main': Permission denied` **Solution :**

   1. Ouvrez [!DNL AndroidManifest.xml] sous le [!DNL CatalogActivity] projet dans l’espace de travail.

   1. Ajouter l&#39;autorisation suivante au [!DNL `AndroidManfest.xml`] fichier :

      ```
      android.permission.READ_LOGS
      ```
