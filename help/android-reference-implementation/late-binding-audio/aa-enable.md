---
description: Vous pouvez intégrer des diffusions audio de remplacement ou à liaison tardive dans votre lecteur en créant un autre gestionnaire de fonctionnalités audio.
title: Intégrer du contenu audio à liaison tardive
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---

# Intégrer du contenu audio à liaison tardive {#integrate-late-binding-audio}

Vous pouvez intégrer des diffusions audio de remplacement ou à liaison tardive dans votre lecteur en créant un autre gestionnaire de fonctionnalités audio.

* Pour créer un autre gestionnaire audio :

  ```java
  AAManager aaManager = new AAManagerOn(); 
  ```

* Pour utiliser ManagerFactory afin d’activer un son alternatif, assurez-vous que la ligne de code suivante figure dans la variable `PlayerFragment.java` fichier :

  ```java
  aaManager = ManagerFactory.getAAManager( 
  <b>true</b>,config, mediaPlayer);
  ```

  Pour désactiver le son alternatif :

  ```java
  aaManager = ManagerFactory.getAAManager( 
  <b>false</b>,config, mediaPlayer);
  ```
