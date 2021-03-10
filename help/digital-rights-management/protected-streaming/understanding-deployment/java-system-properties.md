---
description: Il existe plusieurs propriétés Java System que vous pouvez configurer sur le serveur de licences pour contrôler l’emplacement des fichiers de configuration et journaux.
title: Propriétés du système Java
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---


# Propriétés du système Java{#java-system-properties}

Il existe plusieurs propriétés Java System que vous pouvez configurer sur le serveur de licences pour contrôler l’emplacement des fichiers de configuration et journaux.

Vous pouvez éventuellement configurer les propriétés Java System suivantes :

* *`LicenseServer.ConfigRoot`* — Nom du répertoire contenant les fichiers de configuration du serveur de licences.

   Voir *Fichiers de configuration du serveur de licences* pour plus d’informations sur le contenu de ces fichiers. Si elle n’est pas configurée, la valeur par défaut est `CATALINA_BASE/licenseserver`.

* *LicenseServer.LogRoot*  : nom du  [!DNL logs] répertoire dans lequel se trouvent les journaux d&#39;application du serveur de licences. Si vous n&#39;avez pas modifié le nom de ce répertoire, celui-ci est configuré par défaut comme *LicenseServer.ConfigRoot*.

Si vous utilisez le fichier [!DNL catalina.bat] ou [!DNL catalina.sh] pour début Tomcat, vous pouvez configurer les propriétés système avec la variable d&#39;environnement `JAVA_OPTS`. Toutes les options Java configurées sont automatiquement appliquées lorsque Tomcat début.

Par exemple, vous pouvez configurer la variable d&#39;environnement `JAVA_OPTS` comme suit :

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" 
  -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

