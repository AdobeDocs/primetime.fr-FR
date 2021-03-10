---
title: Propriétés du système Java
description: Propriétés du système Java
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# Propriétés du système Java {#java-system-properties}

Les deux propriétés Java System suivantes peuvent éventuellement être définies pour modifier l’emplacement de la configuration et des fichiers journaux du serveur de licences :

* *LicenseServer.ConfigRoot*  : répertoire contenant tous les fichiers de configuration du serveur de licences. Pour plus d’informations sur le contenu de ces fichiers, voir &quot;[Fichiers de configuration du serveur de licence](../../aaxs-protected-streaming/aaxs-license-server-config-files/aaxs-configuration-directory-structure.md)&quot;. Si elle n’est pas définie, la valeur par défaut est *CATALINA_BASE/concédant de licence*.
* *LicenseServer.LogRoot*  : répertoire du dossier &quot;logs&quot;, où sont écrits les journaux d&#39;application du serveur de licences. Si elle n’est pas définie, la valeur par défaut est *LicenseServer.ConfigRoot*.

Si vous utilisez [!DNL catalina.bat] ou [!DNL catalina.sh] pour début à Tomcat, ces propriétés système peuvent facilement être définies à l&#39;aide de la variable d&#39;environnement `JAVA_OPTS`. Toutes les options Java définies ici seront utilisées au démarrage de Tomcat. Par exemple, définissez :

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

