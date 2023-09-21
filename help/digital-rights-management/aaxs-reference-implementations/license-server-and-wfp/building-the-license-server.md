---
title: Création du serveur de licences
description: Création du serveur de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Création du serveur de licences {#building-the-license-server}

Le serveur de licence de mise en oeuvre de référence comprend des fichiers WAR pour le déploiement du serveur de licences. Il comprend également tout le code source du serveur de licences et un script de build Ant (Référence Implementation\Server\refimpl\build-refimpl.xml) afin que vous puissiez facilement apporter des modifications au code.

>[!NOTE]
>
>Cette étape n’est nécessaire que si vous souhaitez modifier le code source. À des fins d’évaluation, vous pouvez ignorer cette étape et utiliser les fichiers WAR tels qu’expédiés.

Avant d’exécuter le script Ant, modifiez le script pour spécifier les emplacements du SDK Adobe Access, de Tomcat, de MySQL et de Log4J. Ouvrez le fichier build-refimpl.xml dans un éditeur de texte et modifiez les valeurs des propriétés `sdkdir, tomcatdir, mysqldir, and log4jdir`. Pour compiler le code source et créer les fichiers WAR pour l’implémentation de référence, exécutez le script en utilisant `ant -f build-refimpl.xml all` dans le répertoire contenant le script Ant. Une fois le script terminé, une [!DNL refimpl-build/wars] Le répertoire contenant les fichiers WAR du serveur sera créé.
