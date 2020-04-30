---
seo-title: Création du serveur de licences
title: Création du serveur de licences
uuid: d7ca8a8f-c778-41a2-b823-93fac9ab07c5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Création du serveur de licences {#building-the-license-server}

Le serveur de licences d’implémentation de référence comprend des fichiers WAR pour le déploiement du serveur de licences. Il comprend également tout le code source du serveur de licences et un script de création Ant (Référence Implementation\Server\refimpl\build-refimpl.xml) afin que vous puissiez facilement apporter des modifications au code.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Cette étape est nécessaire uniquement si vous souhaitez modifier le code source. À des fins d’évaluation, vous pouvez ignorer cette étape et utiliser les fichiers WAR tels qu’expédiés.

Avant d’exécuter le script Ant, modifiez le script afin de spécifier les emplacements du SDK Adobe Access, de Tomcat, de MySQL et de Log4J. Ouvrez le fichier build-refimpl.xml dans un éditeur de texte et modifiez les valeurs des propriétés `sdkdir, tomcatdir, mysqldir, and log4jdir`. Pour compiler le code source et créer les fichiers WAR pour l’implémentation de référence, exécutez le script en utilisant `ant -f build-refimpl.xml all` le répertoire contenant le script Ant. Une fois le script terminé, un [!DNL refimpl-build/wars] répertoire contenant les fichiers WAR du serveur est créé.
