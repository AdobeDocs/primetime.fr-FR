---
description: 'null'
seo-description: 'null'
seo-title: Déploiement du serveur de licences
title: Déploiement du serveur de licences
uuid: bee7ead1-ed13-4894-80f9-5196bf2f818f
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# Déploiement du serveur de licences{#deploy-the-license-server}

1. Copiez vos fichiers de guerre d’implémentation de référence dans le `webapps` répertoire de votre serveur Tomcat.

   Pour utiliser le serveur de licences d’implémentation de référence tel quel, vous pouvez simplement copier le fichier WAR ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\\flashaccess.war`) du serveur de licences dans le répertoire `webapps` de votre serveur Tomcat.

   Si vous personnalisez le serveur de licences d’implémentation de référence, copiez les fichiers de guerre de serveur que vous avez créés `DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl-build\wars` dans le `webapps` répertoire.

   >[!NOTE]
   >
   >Si vous avez déjà déployé des fichiers WAR de serveur de licences, vous devrez peut-être supprimer les répertoires WAR décompressés dans le répertoire [!DNL webapps] du serveur Tomcat :
   >
   >* [!DNL webapps/flashaccess]
   >* [!DNL webapps/edcws]


   >[!NOTE]
   >
   >Ne déployez pas [!DNL edsws.war] à moins que vous n’ayez besoin d’une compatibilité ascendante avec le contenu FMRMS (Flash Media Rights Management) v1.5. (Il s&#39;agit d&#39;une exigence très rare.)
   >
   >Si vous préférez empêcher Tomcat de décompresser les fichiers WAR, modifiez `server.xml` le répertoire `conf` et définissez `unpackWARs` sur `false`.

1. Copiez tout le contenu du `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources\` répertoire dans votre [!DNL tomcat] répertoire.

   Le [!DNL resources] répertoire comprend :

   * [!DNL flashaccesstools.properties] - Fichier de propriétés du serveur de licences.
   * [!DNL log4j.xml] - Configuration de la journalisation du serveur de licences
   * [!DNL *.pol] - Exemples de fichiers de stratégie DRM.

   De plus, vous pouvez également choisir de copier les fichiers de certification d&#39;Adobe à cet emplacement.

1. Modifiez les paramètres du serveur de licences dans [!DNL flashaccesstools.properties] pour refléter la configuration de votre serveur.

   Au minimum, définissez des valeurs pour les propriétés suivantes :

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

1. Modifiez le `catalina.properties` fichier dans votre `conf` répertoire Tomcat ; ajoutez l’emplacement de votre [!DNL resources] répertoire (ou l’autre emplacement où vous avez stocké votre fichier de propriétés et d’autres fichiers de ressources) à la `shared.loader` propriété.

   Par exemple, si vous avez `flashaccess-refimpl.properties` situé dans [ !DNL [Tomcat home]\resources\] :

   ```
   shared.loader=..\resources
   ```

   Ceci est placé `flashaccess-refimpl.properties` sur le chemin de classe.
1. Assurez-vous que vos autres fichiers de ressources ( [!DNL log4j.xml]fichiers de stratégie, certifications) se trouvent dans le [!DNL resources] répertoire ou se trouvent dans le chemin de classe et leur emplacement spécifié dans [!DNL flashaccess-refimpl.properties].

   Il est probable que vous souhaitiez exécuter initialement `log4j` en mode débogage. Dans [!DNL log4j.xml], définissez `debug` la valeur sur true :

   ```
   <log4j:configuration xmlns:log4j="https://jakarta.apache.org/log4j/"<b>debug="true"</b>>
   ...
   ```

1. Dans le répertoire Tomcat [!DNL bin] , début votre serveur.

   Sous Linux :

   ```
   catalina.sh start
   ```

   Sous Windows :

   ```
   catalina.bat start
   ```
