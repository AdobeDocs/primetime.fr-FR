---
description: Vous pouvez intégrer des flux audio de liaison tardive ou d’autres flux dans votre lecteur en créant un autre gestionnaire de fonctionnalités audio.
seo-description: Vous pouvez intégrer des flux audio de liaison tardive ou d’autres flux dans votre lecteur en créant un autre gestionnaire de fonctionnalités audio.
seo-title: Intégrer le son à liaison tardive
title: Intégrer le son à liaison tardive
uuid: cd2e259a-2af4-4d7b-a856-79bd087e8ca6
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Intégrer le son à liaison tardive {#integrate-late-binding-audio}

Vous pouvez intégrer des flux audio de liaison tardive ou d’autres flux dans votre lecteur en créant un autre gestionnaire de fonctionnalités audio.

* Pour créer un autre gestionnaire audio :

   ```java
   AAManager aaManager = new AAManagerOn(); 
   ```

* Pour utiliser ManagerFactory pour activer des fichiers audio de remplacement, assurez-vous que la ligne de code suivante figure dans le `PlayerFragment.java` fichier :

   ```java
   aaManager = ManagerFactory.getAAManager( 
   <b>true</b>,config, mediaPlayer);
   ```

   Pour désactiver les fichiers audio de remplacement :

   ```java
   aaManager = ManagerFactory.getAAManager( 
   <b>false</b>,config, mediaPlayer);
   ```

