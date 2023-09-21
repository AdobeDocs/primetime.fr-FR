---
title: Présentation du déploiement du serveur de licences et du module de dossiers de contrôle
description: Présentation du déploiement du serveur de licences et du module de dossiers de contrôle
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Présentation du déploiement du serveur de licences et du module de dossiers de contrôle {#deploying-the-license-server-and-watched-folder-packager-overview}

Copiez les fichiers WAR du serveur de licences dans Tomcat [!DNL webapps] répertoire . Si vous avez déjà déployé le fichier WAR, vous devrez peut-être supprimer manuellement les répertoires WAR décompressés ( [!DNL flashaccess], [!DNL edcws], et [!DNL flashaccess-packager] chez Tomcat [!DNL webapps] ). Pour empêcher Tomcat de décompresser des fichiers WAR, modifiez la variable [!DNL server.xml] dans le répertoire conf de Tomcat et définissez la variable `unpackWARs` Attribuer à `false`.

Le fichier de propriétés ( [!DNL flashaccess-refimpl.properties]) doit se trouver sur le chemin d’accès aux classes pour que le serveur charge les propriétés. Copiez ce fichier dans un répertoire et mettez à jour le fichier avec les valeurs appropriées. Modifiez la variable [!DNL catalina.properties] dans le fichier Tomcat [!DNL conf] et ajoutez le répertoire contenant [!DNL flashaccess-refimpl.properties] à la fonction `shared.loader` . La variable [!DNL log4j.xml] pour configurer la journalisation, doit également se trouver sur le chemin d’accès aux classes (voir [!DNL resources\log4j.xml] par exemple).

Le serveur d’implémentation de référence utilise plusieurs fichiers de certificat, fichiers de stratégie et autres ressources. Ces fichiers sont tous situés dans un seul dossier de ressources. Par défaut, le dossier de ressources est [!DNL C:\flashaccess-server-resources], mais cet emplacement peut être modifié dans [!DNL flashaccess-refimpl.properties]. Veillez à copier toutes les ressources requises vers cet emplacement avant de démarrer le serveur.

Pour démarrer Tomcat et le serveur de licences, exécutez `catalina.bat start` de Tomcat [!DNL bin] répertoire .
