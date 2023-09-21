---
description: Il existe plusieurs propriétés système Java que vous pouvez configurer sur le serveur de licences pour contrôler l’emplacement des fichiers de configuration et journaux.
title: Propriétés du système Java
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Propriétés du système Java{#java-system-properties}

Il existe plusieurs propriétés système Java que vous pouvez configurer sur le serveur de licences pour contrôler l’emplacement des fichiers de configuration et journaux.

Vous pouvez éventuellement configurer les propriétés système Java suivantes :

* *`LicenseServer.ConfigRoot`* — Nom du répertoire contenant les fichiers de configuration du serveur de licences.

  Voir *Fichiers de configuration du serveur de licences* pour plus d’informations sur le contenu de ces fichiers. Si elle n’est pas configurée, la valeur par défaut est `CATALINA_BASE/licenseserver`.

* *LicenseServer.LogRoot* — Nom de la variable [!DNL logs] répertoire dans lequel se trouvent les journaux de l’application du serveur de licences. Si vous n’avez pas modifié le nom de ce répertoire, son nom est configuré comme *LicenseServer.ConfigRoot* par défaut.

Si vous utilisez la variable [!DNL catalina.bat] ou [!DNL catalina.sh] pour démarrer Tomcat, vous pouvez configurer les propriétés du système avec la propriété `JAVA_OPTS` Variable d’environnement. Toutes les options Java configurées sont automatiquement appliquées au démarrage de Tomcat.

Par exemple, vous pouvez configurer la variable `JAVA_OPTS` Variable d’environnement comme suit :

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" 
  -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```
