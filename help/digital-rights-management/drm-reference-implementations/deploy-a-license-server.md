---
title: Déploiement du serveur de licences
description: Déploiement du serveur de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Déploiement du serveur de licences{#deploy-the-license-server}

1. Copiez les fichiers war d’implémentation de référence dans la `webapps` sur votre serveur Tomcat.

   Pour utiliser le serveur de licence de mise en oeuvre de référence tel quel, vous pouvez simplement copier le fichier WAR du serveur de licences ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\\flashaccess.war`) à la variable `webapps` sur votre serveur Tomcat.

   Si vous personnalisez le serveur de licence de mise en oeuvre de référence, copiez les fichiers war du serveur à partir desquels vous avez créé `DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl-build\wars` à la fonction `webapps` répertoire .

   >[!NOTE]
   >
   >Si vous avez déjà déployé des fichiers WAR du serveur de licences, vous devrez peut-être supprimer les répertoires WAR décompressés dans la variable [!DNL webapps] sur le serveur Tomcat :
   >
   >* [!DNL webapps/flashaccess]
   >* [!DNL webapps/edcws]

   >[!NOTE]
   >
   >Ne pas déployer [!DNL edsws.war] sauf si vous avez besoin d’une compatibilité descendante avec le contenu FMRMS (Flash Media Rights Management) v1.5. (C’est une exigence très rare.)
   >
   >Si vous préférez empêcher Tomcat de décompresser les fichiers WAR, modifiez `server.xml` dans le `conf` répertoire et définition `unpackWARs` to `false`.

1. Copiez l’intégralité du contenu de la fonction `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources\` dans votre [!DNL tomcat] répertoire .

   La variable [!DNL resources] comprend :

   * [!DNL flashaccesstools.properties] - Le fichier de propriétés du serveur de licences.
   * [!DNL log4j.xml] - Configuration de la journalisation du serveur de licences
   * [!DNL *.pol] - Exemples de fichiers de stratégie DRM.

   Vous pouvez également choisir de copier les fichiers de certification d’Adobe vers cet emplacement.

1. Modification des paramètres du serveur de licences dans [!DNL flashaccesstools.properties] pour refléter la configuration de votre serveur.

   Définissez au minimum les valeurs des propriétés suivantes :

   * `config.resourcesDirectory`
   * `HandlerConfiguration.ServerTransportCredential`
   * `HandlerConfiguration.ServerTransportCredential.password`
   * `LicenseHandler.ServerCredential`
   * `LicenseHandler.ServerCredential.password`
   * `MetaDataConverter.SignatureParameters.ServerCredential`
   * `MetaDataConverter.SignatureParameters.ServerCredential.password`
   * `V2KeyParameters.LicenseServerUrl`
   * `V2KeyParameters.KeyOptions.AsymmetricKeyOptions.Certificate`
   * V2KeyParameters.LicenseServerTransportCertificate

1. Modifiez la variable `catalina.properties` fichier dans votre Tomcat `conf` , ajoutez l’emplacement de votre [!DNL resources] le répertoire (ou l’autre emplacement où vous avez stocké votre fichier de propriétés et d’autres fichiers de ressources) vers la propriété `shared.loader` .

   Par exemple, si vous avez `flashaccess-refimpl.properties` situé dans [!DNL [Accueil de Tomcat]\resources\]:

   ```
   shared.loader=..\resources
   ```

   Cet emplacement `flashaccess-refimpl.properties` sur le chemin d’accès aux classes.
1. Assurez-vous que vos autres fichiers de ressources ( [!DNL log4j.xml], les fichiers de stratégie, les certifications) se trouvent dans la variable [!DNL resources] ou se trouvent dans le chemin d’accès aux classes et leur emplacement spécifiés dans [!DNL flashaccess-refimpl.properties].

   Il est probable que vous souhaitiez exécuter initialement `log4j` en mode debug . Dans [!DNL log4j.xml], définit `debug` à true :

   ```
   <log4j:configuration xmlns:log4j="https://jakarta.apache.org/log4j/"<b>debug="true"</b>>
   ...
   ```

1. Du Tomcat [!DNL bin] , démarrez votre serveur.

   Sous Linux :

   ```
   catalina.sh start
   ```

   Sous Windows :

   ```
   catalina.bat start
   ```
