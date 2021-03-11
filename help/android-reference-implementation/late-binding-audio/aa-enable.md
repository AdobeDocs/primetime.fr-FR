---
description: Vous pouvez intégrer des flux audio de liaison tardive ou alternatifs dans votre lecteur en créant un autre gestionnaire de fonctionnalités audio.
title: Intégration d’un fichier audio à liaison tardive
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---


# Intégrer l’audio à liaison tardive {#integrate-late-binding-audio}

Vous pouvez intégrer des flux audio de liaison tardive ou alternatifs dans votre lecteur en créant un autre gestionnaire de fonctionnalités audio.

* Pour créer un autre gestionnaire audio :

   ```java
   AAManager aaManager = new AAManagerOn(); 
   ```

* Pour utiliser ManagerFactory pour activer des fichiers audio de remplacement, assurez-vous que la ligne de code suivante figure dans le fichier `PlayerFragment.java` :

   ```java
   aaManager = ManagerFactory.getAAManager( 
   <b>true</b>,config, mediaPlayer);
   ```

   Pour désactiver les fichiers audio de remplacement :

   ```java
   aaManager = ManagerFactory.getAAManager( 
   <b>false</b>,config, mediaPlayer);
   ```

