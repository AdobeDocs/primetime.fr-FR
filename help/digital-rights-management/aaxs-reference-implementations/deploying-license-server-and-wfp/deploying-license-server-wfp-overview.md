---
seo-title: Présentation du déploiement du serveur de licences et du gestionnaire de dossiers de contrôle
title: Présentation du déploiement du serveur de licences et du gestionnaire de dossiers de contrôle
uuid: 4b71f2f4-f971-4382-ae41-171f7dfdfe21
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Présentation du déploiement du serveur de licences et du gestionnaire de dossiers de contrôle {#deploying-the-license-server-and-watched-folder-packager-overview}

Copiez les fichiers WAR du serveur de licences dans le [!DNL webapps] répertoire de Tomcat. Si vous avez déjà déployé le fichier WAR, vous devrez peut-être supprimer manuellement les répertoires WAR décompressés ( [!DNL flashaccess], [!DNL edcws]et [!DNL flashaccess-packager] dans le [!DNL webapps] répertoire de Tomcat). Pour empêcher Tomcat de décompresser des fichiers WAR, modifiez le [!DNL server.xml] fichier dans le répertoire conf de Tomcat et définissez l’ `unpackWARs` attribut sur `false`.

Le fichier de propriétés ( [!DNL flashaccess-refimpl.properties]) doit se trouver sur le chemin de classe pour que le serveur charge les propriétés. Copiez ce fichier dans un répertoire et mettez à jour le fichier avec les valeurs appropriées. Modifiez le [!DNL catalina.properties] fichier dans le [!DNL conf] répertoire de Tomcat et ajoutez le répertoire contenant [!DNL flashaccess-refimpl.properties] à la propriété `shared.loader` . Le [!DNL log4j.xml] fichier de configuration de la journalisation doit également se trouver sur le chemin de classe (voir [!DNL resources\log4j.xml] un exemple).

Le serveur d’implémentation de référence utilise plusieurs fichiers de certificat, fichiers de stratégie et autres ressources. Ces fichiers se trouvent tous dans un dossier de ressources unique. Par défaut, le dossier de ressources est [!DNL C:\flashaccess-server-resources]défini, mais cet emplacement peut être modifié dans [!DNL flashaccess-refimpl.properties]. Veillez à copier toutes les ressources requises vers cet emplacement avant de démarrer le serveur.

Pour à Tomcat et au serveur de licences, exécutez `catalina.bat start` à partir du [!DNL bin] répertoire de Tomcat.
