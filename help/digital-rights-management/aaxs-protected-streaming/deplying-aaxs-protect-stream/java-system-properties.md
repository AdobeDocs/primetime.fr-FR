---
title: Propriétés du système Java
description: Propriétés du système Java
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# Propriétés du système Java {#java-system-properties}

Les deux propriétés suivantes du système Java peuvent éventuellement être définies pour modifier l’emplacement de la configuration et des fichiers journaux du serveur de licences :

* *LicenseServer.ConfigRoot* — Répertoire contenant tous les fichiers de configuration du serveur de licences. Pour plus d’informations sur le contenu de ces fichiers, voir &quot;[Fichiers de configuration du serveur de licences](../../aaxs-protected-streaming/aaxs-license-server-config-files/aaxs-configuration-directory-structure.md)&quot;. Si elle n’est pas définie, la valeur par défaut est *CATALINA_BASE/conceserver*.
* *LicenseServer.LogRoot* — Répertoire du dossier &quot;logs&quot;, où sont écrits les journaux de l’application du serveur de licences. Si elle n’est pas définie, la valeur par défaut est *LicenseServer.ConfigRoot*.

Si vous utilisez [!DNL catalina.bat] ou [!DNL catalina.sh] Pour démarrer Tomcat, ces propriétés système peuvent facilement être définies à l’aide de la propriété `JAVA_OPTS` Variable d’environnement. Toutes les options Java définies ici seront utilisées au démarrage de Tomcat. Par exemple, définissez :

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```
