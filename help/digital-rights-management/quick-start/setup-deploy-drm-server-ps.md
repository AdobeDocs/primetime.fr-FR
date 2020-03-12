---
seo-title: Configuration et déploiement du serveur pour la diffusion en continu protégée
title: Configuration et déploiement du serveur pour la diffusion en continu protégée
uuid: 300a1b63-0bf0-48a8-977d-212563025c19
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Configuration et déploiement du serveur pour la diffusion en continu protégée {#set-up-and-deploy-the-server-for-protected-streaming}

1. Configurez le dossier de configuration sur le DVD DRM Primetime :

   `\Adobe Access Server for Protected Streaming\configs\`
1. Copiez le `configs` dossier d’exemple dans votre dossier `<Tomcat_installation_dir>` et renommez le dossier copié en `licenseserver`tant que tel.

   Le chemin d’accès au dossier configs doit maintenant être `<Tomcat_install_dir>\licenseserver\`.
1. Exécutez `Scrambler.bat` pour obtenir les mots de passe chiffrés pour les fichiers PFX du serveur de transport et de licence dans le `<DVD>` répertoire DRM Primetime `\Adobe Access Server for Protected Streaming\` :

   * `Scrambler.bat <Adobe-provided transport credential password>`
   * `Scrambler.bat <Adobe-provided license server credential password>`

1. Copiez les fichiers PFX dans le `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\<tenant-name>\` répertoire.
1. Modifiez la configuration du client correspondante dans `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\sampletenant\flashaccess-tenant.xml`, avec les paramètres suivants :

   ```
   Configuration|Tenant|Credentials|TransportCredential|File|path=<filename-transport-credential-PFX> 
   Configuration|Tenant|Credentials|TransportCredential|File|password=<scrambled-transportcredential-password> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|path=<fielname-license-servercredential-PFX> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|password=<scrambled-license-servercredential-password>
   ```

1. Exécutez l’ `Validator.bat` utilitaire pour vérifier que la configuration est valide :

   ```
   Validator.bat -g -r <absolute-path-to TomcatInstallDir\licenseserver>
   ```

1. Copiez le `flashaccessserver.war` fichier du CD dans le `<TomcatInstallDir>\webapps\` répertoire.
1. Si Tomcat est en cours d’exécution, arrêtez l’instance Tomcat en cours d’exécution en appuyant `<CTRL-C>` sur la fenêtre de commande (si elle a été lancée à partir de la fenêtre de commande). Vous pouvez également arrêter le serveur à partir de l’application des services Windows si Tomcat a été installé en tant que service Windows.
1. Pour à Tomcat, saisissez la commande suivante :

   ```
   <TomcatInstallDir>\bin\catalina run
   ```

1. Pour vérifier la configuration, saisissez l’URL suivante dans un navigateur :

   ```
    https://<LicenseServer>:8080/flashaccessserver/flashaccess/license/v2
   ```
