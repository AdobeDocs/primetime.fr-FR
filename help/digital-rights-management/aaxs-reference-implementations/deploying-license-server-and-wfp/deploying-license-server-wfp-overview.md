---
seo-title: Présentation du déploiement du serveur de licences et du gestionnaire de dossiers de contrôle
title: Présentation du déploiement du serveur de licences et du gestionnaire de dossiers de contrôle
uuid: 4b71f2f4-f971-4382-ae41-171f7dfdfe21
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# Présentation du déploiement du serveur de licences et du gestionnaire de dossiers de contrôle {#deploying-the-license-server-and-watched-folder-packager-overview}

Copiez les fichiers WAR du serveur de licences dans le répertoire [!DNL webapps] de Tomcat. Si vous avez déjà déployé le fichier WAR, vous devrez peut-être supprimer manuellement les répertoires WAR non compressés ( [!DNL flashaccess], [!DNL edcws] et [!DNL flashaccess-packager] dans le répertoire [!DNL webapps] de Tomcat). Pour empêcher Tomcat de décompresser les fichiers WAR, modifiez le fichier [!DNL server.xml] dans le répertoire conf de Tomcat et définissez l&#39;attribut `unpackWARs` sur `false`.

Le fichier de propriétés ( [!DNL flashaccess-refimpl.properties]) doit se trouver sur le chemin de classe pour que le serveur puisse charger les propriétés. Copiez ce fichier dans un répertoire et mettez à jour le fichier avec les valeurs appropriées. Modifiez le fichier [!DNL catalina.properties] dans le répertoire [!DNL conf] de Tomcat et ajoutez le répertoire contenant [!DNL flashaccess-refimpl.properties] à la propriété `shared.loader`. Le fichier [!DNL log4j.xml] pour configurer la journalisation doit également se trouver sur le chemin de classe (voir [!DNL resources\log4j.xml] pour un exemple).

Le serveur d’implémentation de référence utilise plusieurs fichiers de certificat, fichiers de stratégie et autres ressources. Ces fichiers se trouvent tous dans un dossier de ressources unique. Par défaut, le dossier de ressources est [!DNL C:\flashaccess-server-resources], mais cet emplacement peut être modifié dans [!DNL flashaccess-refimpl.properties]. Veillez à copier toutes les ressources requises à cet emplacement avant de démarrer le serveur.

Pour début Tomcat et le serveur de licences, exécutez `catalina.bat start` à partir du répertoire [!DNL bin] de Tomcat.
