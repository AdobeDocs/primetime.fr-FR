---
description: Il existe plusieurs propriétés Java System que vous pouvez configurer sur le serveur de licences pour contrôler l’emplacement des fichiers de configuration et des fichiers journaux.
seo-description: Il existe plusieurs propriétés Java System que vous pouvez configurer sur le serveur de licences pour contrôler l’emplacement des fichiers de configuration et des fichiers journaux.
seo-title: Propriétés du système Java
title: Propriétés du système Java
uuid: d8c72359-bf61-47e0-9cd5-b21225d5fe49
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Propriétés du système Java{#java-system-properties}

Il existe plusieurs propriétés Java System que vous pouvez configurer sur le serveur de licences pour contrôler l’emplacement des fichiers de configuration et des fichiers journaux.

Vous pouvez éventuellement configurer les propriétés Java System suivantes :

* *`LicenseServer.ConfigRoot`* — Nom du répertoire contenant les fichiers de configuration du serveur de licences.

   Voir Fichiers *de configuration du serveur de* licence pour plus d’informations sur le contenu de ces fichiers. Si elle n’est pas configurée, la valeur par défaut est `CATALINA_BASE/licenseserver`.

* *LicenseServer.LogRoot* — Nom du [!DNL logs] répertoire dans lequel se trouvent les journaux d’application du serveur de licences. Si vous n’avez pas modifié le nom de ce répertoire, le nom de ce répertoire est configuré comme *LicenseServer.ConfigRoot* par défaut.

Si vous utilisez le [!DNL catalina.bat] fichier ou [!DNL catalina.sh] pour à Tomcat, vous pouvez configurer les propriétés du système avec la variable `JAVA_OPTS` . Toutes les options Java que vous configurez sont automatiquement appliquées lorsque le Tomcat .

Vous pouvez, par exemple, configurer la variable   de l’comme suit : `JAVA_OPTS`

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" 
  -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

