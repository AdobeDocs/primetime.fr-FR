---
seo-title: Propriétés du système Java
title: Propriétés du système Java
uuid: ad1f3d9b-7d95-4e19-a0f8-fd7d4dd4dc32
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Propriétés du système Java {#java-system-properties}

Les deux propriétés Java System suivantes peuvent être éventuellement définies pour modifier l’emplacement de la configuration et des fichiers journaux du serveur de licences :

* *LicenseServer.ConfigRoot* — Répertoire contenant tous les fichiers de configuration du serveur de licences. Pour plus d’informations sur le contenu de ces fichiers, voir &quot;Fichiers[de configuration du serveur de](../../aaxs-protected-streaming/aaxs-license-server-config-files/aaxs-configuration-directory-structure.md)licence&quot;. Si elle n’est pas définie, la valeur par défaut est *CATALINA_BASE/concédant* de licence.
* *LicenseServer.LogRoot* — Répertoire du dossier &quot;logs&quot;, où sont écrits les journaux d’application du serveur de licences. Si elle n’est pas définie, la valeur par défaut est *LicenseServer.ConfigRoot*.

Si vous utilisez [!DNL catalina.bat] ou [!DNL catalina.sh] pour Tomcat, vous pouvez facilement définir ces propriétés système à l’aide de la variable `JAVA_OPTS` . Toutes les options Java définies ici seront utilisées au démarrage de Tomcat. Par exemple, set :

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

