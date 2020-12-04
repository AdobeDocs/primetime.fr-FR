---
description: Utilisez la fonction CEK externe pour vendre et assembler des licences à l’aide de votre fichier CKMS existant.
seo-description: Utilisez la fonction CEK externe pour vendre et assembler des licences à l’aide de votre fichier CKMS existant.
seo-title: Utilisation du CEK externe pour diffuser et assembler des licences
title: Utilisation du CEK externe pour diffuser et assembler des licences
uuid: 1bfd8c6c-4ae9-47de-8247-085b5360127d
translation-type: tm+mt
source-git-commit: fe9493d610bc6fb97d30351c707b73cda92c67a0
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---


# Utilisation du CEK externe pour distribuer et compresser des licences{#using-external-cek-to-vend-and-package-licenses}

Utilisez la fonction CEK externe pour vendre et assembler des licences à l’aide de votre fichier CKMS existant.

## EncryptContentWithExternalKey.java

Il s’agit d’un outil de ligne de commande qui permet de chiffrer AAXS une vidéo et de créer des métadonnées qui *ne contiendront pas* le CEK (protégé par un certificat public du serveur de licences AAXS). L’outil incorpore plutôt un identifiant CEK dans les métadonnées de la vidéo.

Lors de l’acquisition de la licence, le serveur de licences AAXS observe un indicateur dans les métadonnées indiquant que ce contenu a été protégé à l’aide d’un CEK externe. Le serveur de licences va extraire l’identifiant CEK des métadonnées, puis requête un référentiel sécurisé/CKMS pour récupérer le CEK approprié.

## Processus de création de package

1. Vérifiez que vous utilisez Java 1.6.0_24 ou version ultérieure.
1. Pour afficher l&#39;utilisation de l&#39;outil : `java -jar AdobePackager_ExternalCEK.jar`
1. Pour compresser du contenu :

   ```
   java -jar AdobePackager_ExternalCEK.jar sample.flv encrypted.flv abc abcdef0123456789 
       policy.pol https://path-to-your-server:8090 <license-server-public-cert.pem> 
       <license-server-private-key.pfx> <private-key-password>
   ```

>[!NOTE]
>
>* Le code source Java peut être créé à l&#39;aide de l&#39;ANT `build-samples.xml` inclus.
>* Le SDK Flash Access ( `adobe-flashaccess-sdk.jar`) doit se trouver sur le chemin de classe

>



## Processus du serveur

1. Configurez la mise en oeuvre des références.
1. S’il en existe, nettoyez les déploiements d’implémentation de référence précédents :

   1. `delete <tomcat>\work\Catalina\*.*`
   1. `delete <tomcat>\conf\Catalina\*.*`
   1. `delete <tomcat>\logs\*.*`

1. Vérifiez qu’il existe un fichier [!DNL CEKDepot.properties] à côté de votre [!DNL flashaccess-refimpl.properties]

1. Lancer une demande de licence d&#39;un lecteur Adobe Primetime
1. Observez les journaux Impl de référence pour obtenir un résultat similaire :

   ```
   DEBUG [com.adobe.flashaccess.refimpl.web.RefImplLicenseReqHandler.REQUESTS] 
     Used CEK ID:{abc} to retrieve CEK: {abcdef0123456789} from depot
   ```

   1. Vous devrez peut-être modifier vos paramètres [!DNL log4j.xml] pour vous connecter à un niveau `DEBUG` ( `INFO` est défini par défaut).

## Problèmes connus

Aucun
