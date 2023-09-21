---
title: Configuration et déploiement du serveur pour la diffusion en continu protégée
description: Configuration et déploiement du serveur pour la diffusion en continu protégée
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Configuration et déploiement du serveur pour la diffusion en continu protégée {#set-up-and-deploy-the-server-for-protected-streaming}

1. Configurez le dossier de configuration sur le DVD Primetime DRM :

   `\Adobe Access Server for Protected Streaming\configs\`
1. Copier l’exemple `configs` dans votre dossier `<Tomcat_installation_dir>` et renommez le dossier copié en `licenseserver`.

   Le chemin d’accès au dossier configurations doit maintenant être : `<Tomcat_install_dir>\licenseserver\`.
1. Exécuter `Scrambler.bat` Obtention des mots de passe cryptés pour les fichiers PFX du serveur de transport et de licences dans Primetime DRM `<DVD>` `\Adobe Access Server for Protected Streaming\` directory:

   * `Scrambler.bat <Adobe-provided transport credential password>`
   * `Scrambler.bat <Adobe-provided license server credential password>`

1. Copiez les fichiers PFX dans le `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\<tenant-name>\` répertoire .
1. Modifiez la configuration de tenant correspondante dans `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\sampletenant\flashaccess-tenant.xml`, avec les paramètres suivants :

   ```
   Configuration|Tenant|Credentials|TransportCredential|File|path=<filename-transport-credential-PFX> 
   Configuration|Tenant|Credentials|TransportCredential|File|password=<scrambled-transportcredential-password> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|path=<fielname-license-servercredential-PFX> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|password=<scrambled-license-servercredential-password>
   ```

1. Exécutez la variable `Validator.bat` pour vérifier que la configuration est valide :

   ```
   Validator.bat -g -r <absolute-path-to TomcatInstallDir\licenseserver>
   ```

1. Copiez le `flashaccessserver.war` du CD au `<TomcatInstallDir>\webapps\` répertoire .
1. Si Tomcat est en cours d’exécution, arrêtez l’instance Tomcat en cours d’exécution en appuyant sur `<CTRL-C>` dans la fenêtre de commande (si elle a été lancée à partir de la fenêtre de commande). Vous pouvez également arrêter le serveur à partir de l’application Windows Services si Tomcat a été installé en tant que service Windows.
1. Pour démarrer Tomcat, saisissez la commande suivante :

   ```
   <TomcatInstallDir>\bin\catalina run
   ```

1. Pour vérifier la configuration, saisissez l’URL suivante dans un navigateur :

   ```
    https://<LicenseServer>:8080/flashaccessserver/flashaccess/license/v2
   ```
