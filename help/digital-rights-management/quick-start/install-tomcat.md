---
seo-title: Installer Tomcat
title: Installer Tomcat
uuid: f7663eda-ad18-4a6e-bb9f-01c74721b047
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# Installer Tomcat {#install-tomcat}

Vous devez installer Tomcat sur les deux serveurs.
1. Installez Tomcat à partir du répertoire [ !DNL \Third Party\Tomcat\6.0.18\] sur le DVD d’installation.

   >[!NOTE]
   >
   >Assurez-vous que Tomcat est installé à un emplacement où il n’y a aucun espace dans le chemin. Vous pouvez entrer `C:\Program Files\Tomcat`, mais pas `C:\Tomcat\`.

1. Pour début Tomcat, entrez `TomcatInstallDir>\bin\catalina.bat run`.
1. Pour vérifier l&#39;installation, accédez au landing page Tomcat en entrant `https://<Hostname>:8080/`.
1. Créez un `crossdomain.xml` fichier et importez-le dans le `<TomcatInstallDir>\webapps\ROOT\` répertoire.

   Vous pouvez également copier un fichier à partir du `https://drmtest2.adobe.com/crossdomain.xml` répertoire.
