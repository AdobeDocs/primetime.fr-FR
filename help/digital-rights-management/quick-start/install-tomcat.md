---
title: Installer Tomcat
description: Installer Tomcat
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---


# Installer Tomcat {#install-tomcat}

Vous devez installer Tomcat sur les deux serveurs.
1. Installez Tomcat à partir du répertoire [!DNL \Third Party\Tomcat\6.0.18\] sur le DVD d’installation.

   >[!NOTE]
   >
   >Assurez-vous que Tomcat est installé à un emplacement où il n’y a aucun espace dans le chemin. Vous pouvez entrer `C:\Program Files\Tomcat`, mais pas `C:\Tomcat\`.

1. Pour début Tomcat, saisissez `TomcatInstallDir>\bin\catalina.bat run`.
1. Pour vérifier l&#39;installation, accédez au landing page Tomcat en entrant `https://<Hostname>:8080/`.
1. Créez un fichier `crossdomain.xml` et importez-le dans le répertoire `<TomcatInstallDir>\webapps\ROOT\`.

   Vous pouvez également copier un fichier du répertoire `https://drmtest2.adobe.com/crossdomain.xml`.
