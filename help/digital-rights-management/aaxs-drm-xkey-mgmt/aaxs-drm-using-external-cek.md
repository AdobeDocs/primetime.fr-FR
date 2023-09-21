---
description: Utilisez la fonction External CEK pour vendre et regrouper des licences à l’aide de votre fichier CKMS existant.
title: Utilisation du CEK externe pour diffuser et regrouper des licences
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Utilisation du CEK externe pour diffuser et regrouper des licences{#using-external-cek-to-vend-and-package-licenses}

Utilisez la fonction External CEK pour vendre et regrouper des licences à l’aide de votre fichier CKMS existant.

## EncryptContentWithExternalKey.java

Il s’agit d’un outil de ligne de commande qui chiffrera AAXS une vidéo et créera des métadonnées qui *not* contiennent le CEK (protégé par un certificat public de serveur de licences AAXS). À la place, l’outil incorpore un identifiant CEK dans les métadonnées de la vidéo.

Pendant l’acquisition de la licence, le serveur de licences AAXS observe un indicateur dans les métadonnées indiquant que ce contenu a été protégé à l’aide d’un CEK externe. Le serveur de licences extrait l’ID du CEK des métadonnées, puis effectue une requête sur un référentiel/CKMS sécurisé pour récupérer le CEK approprié.

## Processus de groupement

1. Vérifiez que vous utilisez Java 1.6.0_24 ou version ultérieure.
1. Pour afficher l’utilisation de l’outil : `java -jar AdobePackager_ExternalCEK.jar`
1. Pour regrouper le contenu :

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

## Workflow du serveur

1. Configurez l’implémentation de référence.
1. S’il en existe, nettoyez les déploiements précédents d’implémentation de référence :

   1. `delete <tomcat>\work\Catalina\*.*`
   1. `delete <tomcat>\conf\Catalina\*.*`
   1. `delete <tomcat>\logs\*.*`

1. Vérifiez qu’il existe une [!DNL CEKDepot.properties] fichier avec votre [!DNL flashaccess-refimpl.properties]

1. Lancement d’une demande de licence à partir d’un lecteur Adobe Primetime
1. Observez les journaux Impl des Réf pour une chose similaire à :

   ```
   DEBUG [com.adobe.flashaccess.refimpl.web.RefImplLicenseReqHandler.REQUESTS] 
     Used CEK ID:{abc} to retrieve CEK: {abcdef0123456789} from depot
   ```

   1. Vous devrez peut-être modifier la variable [!DNL log4j.xml] paramètres de connexion à un `DEBUG` niveau ( `INFO` est défini par défaut)

## Problèmes connus

Aucun
