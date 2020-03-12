---
description: Utilisez la fonction de CEK externe pour vendre et assembler des licences à l’aide de votre fichier CKMS existant.
seo-description: Utilisez la fonction de CEK externe pour vendre et assembler des licences à l’aide de votre fichier CKMS existant.
seo-title: Utilisation du CEK externe pour valider et compresser des licences
title: Utilisation du CEK externe pour valider et compresser des licences
uuid: 1bfd8c6c-4ae9-47de-8247-085b5360127d
translation-type: tm+mt
source-git-commit: fe9493d610bc6fb97d30351c707b73cda92c67a0

---


# Utilisation du CEK externe pour valider et compresser des licences{#using-external-cek-to-vend-and-package-licenses}

Utilisez la fonction de CEK externe pour vendre et assembler des licences à l’aide de votre fichier CKMS existant.

## EncryptContentWithExternalKey.java

Il s’agit d’un outil de ligne de commande qui permet de chiffrer une vidéo au format AAXS et de créer des métadonnées *ne contenant pas* le CEK (protégé par un certificat public du serveur de licences AAXS). L’outil incorpore plutôt un identifiant CEK dans les métadonnées de la vidéo.

Lors de l’acquisition de la licence, le serveur de licences AAXS observe un indicateur dans les métadonnées indiquant que ce contenu a été protégé à l’aide d’un CEK externe. Le serveur de licences extrait l’ID CEK des métadonnées, puis un référentiel sécurisé/CKMS pour récupérer le CEK approprié.

## Processus de création de package

1. Vérifiez que vous utilisez Java 1.6.0_24 ou version ultérieure.
1. Pour afficher l’utilisation de l’outil : `java -jar AdobePackager_ExternalCEK.jar`
1. Pour compresser du contenu :

   ```
   java -jar AdobePackager_ExternalCEK.jar sample.flv encrypted.flv abc abcdef0123456789 
       policy.pol https://path-to-your-server:8090 <license-server-public-cert.pem> 
       <license-server-private-key.pfx> <private-key-password>
   ```

>[!NOTE]
>
>* Le code source Java peut être créé à l’aide de l’ANT inclus. `build-samples.xml`
>* Le SDK Flash Access ( `adobe-flashaccess-sdk.jar`) doit se trouver sur le chemin de classe
>



## Processus du serveur

1. Configurez l’implémentation des références.
1. Le cas échéant, nettoyez les déploiements d’implémentation de référence précédents :

   1. `delete <tomcat>\work\Catalina\*.*`
   1. `delete <tomcat>\conf\Catalina\*.*`
   1. `delete <tomcat>\logs\*.*`

1. Vérifiez qu’il existe un [!DNL CEKDepot.properties] fichier à côté de votre [!DNL flashaccess-refimpl.properties]

1. Lancer une demande de licence à partir d’un lecteur Adobe Primetime
1. Observez les journaux Impl de référence pour obtenir un résultat similaire à :

   ```
   DEBUG [com.adobe.flashaccess.refimpl.web.RefImplLicenseReqHandler.REQUESTS] 
     Used CEK ID:{abc} to retrieve CEK: {abcdef0123456789} from depot
   ```

   1. Vous devrez peut-être modifier vos [!DNL log4j.xml] paramètres pour vous connecter à un `DEBUG` niveau ( `INFO` est défini par défaut).

## Problèmes connus

Aucun
