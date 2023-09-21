---
title: Installer Tomcat
description: Installer Tomcat
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# Installer Tomcat {#install-tomcat}

Vous devez installer Tomcat sur les deux serveurs.
1. Installez Tomcat à partir du [!DNL \Third Party\Tomcat\6.0.18\] sur le DVD d’installation.

   >[!NOTE]
   >
   >Assurez-vous que Tomcat est installé à un emplacement où il n’y a aucun espace dans le chemin. Vous pouvez saisir `C:\Program Files\Tomcat`, mais pas `C:\Tomcat\`.

1. Pour démarrer Tomcat, saisissez `TomcatInstallDir>\bin\catalina.bat run`.
1. Pour vérifier l’installation, accédez à la landing page Tomcat en saisissant `https://<Hostname>:8080/`.
1. Créez un `crossdomain.xml` et placez le fichier dans le `<TomcatInstallDir>\webapps\ROOT\` répertoire .

   Vous pouvez également copier un fichier à partir de la fonction `https://drmtest2.adobe.com/crossdomain.xml` répertoire .
