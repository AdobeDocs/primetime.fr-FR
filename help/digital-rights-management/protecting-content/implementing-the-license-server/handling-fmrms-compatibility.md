---
description: Gestion de la compatibilité FMRMS
seo-description: Gestion de la compatibilité FMRMS
seo-title: Mise à niveau des clients
title: Mise à niveau des clients
uuid: c32ee087-2edf-4d11-be36-e2b31f3769de
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---


# Gestion de la compatibilité FMRMS {#handling-fmrms-compatibility}

Il existe deux types de requêtes liées à la compatibilité de Flash Media Rights Management Server 1.x. Un type de requête est utilisé pour inviter les clients 1.x à effectuer la mise à niveau vers un runtime qui prend en charge Adobe Primetime DRM 2.0 ou version ultérieure. Une autre est utilisée pour mettre à jour les métadonnées 1.x au format DRM Primetime avant qu’une licence ne puisse être demandée. La prise en charge de ces requêtes n’est requise que si vous avez précédemment déployé un contenu utilisant FMRMS 1.0 ou 1.5.

## Mise à niveau des clients {#upgrading-clients}

Si un client FMRMS 1.x contacte un serveur DRM Adobe Primetime, le serveur doit demander au client de procéder à la mise à niveau.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* L’URL de demande est &quot;*URL de base à partir du contenu 1.x*&quot; + &quot; [!DNL /edcws/services/urn:EDCLicenseService]&quot;

   Contrairement à d’autres gestionnaires de requêtes Adobe Primetime, ce gestionnaire n’offre pas d’accès aux informations de requête et n’exige pas la définition de données de réponse. Créez une instance de `FMRMSv1RequestHandler`, puis appelez `close()`

## Mise à niveau des métadonnées {#upgrading-metadata}

Si un client Adobe Access rencontre le contenu fourni avec Flash Media Rights Management Server 1.x, il extrait les métadonnées de chiffrement du contenu et les envoie au serveur. Le serveur convertit les métadonnées FMRMS 1.x au format Adobe Access et les renvoie au client. Le client envoie ensuite les métadonnées mises à jour dans une demande de licence d’accès aux Adobes standard.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`.
* L’URL de demande est &quot;*URL de base à partir du contenu 1.x*&quot; +&quot;/flashaccess/headerconversion/v1&quot;.

La conversion des métadonnées peut être effectuée à la volée lorsque le serveur reçoit les anciennes métadonnées du client. Le serveur peut également prétraiter l’ancien contenu et stocker les métadonnées converties ; dans ce cas, lorsque le client demande de nouvelles métadonnées, le serveur doit simplement récupérer les nouvelles métadonnées correspondant à l’identifiant de licence des anciennes métadonnées.

Pour convertir les métadonnées, le serveur doit effectuer les opérations suivantes :

* Get `LiveCycleKeyMetaData`. Pour préconvertir les métadonnées, `LiveCycleKeyMetaData` peut être obtenu à partir d’un fichier compressé de la version 1.x à l’aide de `MediaEncrypter.examineEncryptedContent()`. Les métadonnées sont également incluses dans la demande de conversion de métadonnées ( `FMRMSv1MetadataHandler.getOriginalMetadata()`).
* Récupérez l’identifiant de licence à partir des anciennes métadonnées et recherchez la clé de chiffrement et les stratégies (ces informations figuraient à l’origine dans la base de données Adobe LiveCycle ES. Les stratégies LiveCycle ES doivent être converties en stratégies Adobe Access 2.0.) L’implémentation de référence comprend des scripts et des exemples de code pour la conversion des stratégies et l’exportation des informations de licence à partir de LiveCycle ES.
* Renseignez l’objet `V2KeyParameters` (que vous récupérez en appelant `MediaEncrypter.getKeyParameters()`).
* Chargez `SigningCredential`, qui correspond aux informations d’identification du packager émises par l’Adobe utilisé pour signer les métadonnées de chiffrement. Récupérez l’objet `SignatureParameters` en appelant `MediaEncrypter.getSignatureParameters()` et renseignez les informations d’identification de signature.
* Appelez `MetaDataConverter.convertMetadata()` pour obtenir le `V2ContentMetaData`.
* Appelez `V2ContentMetaData.getBytes()` et stockez-les pour une utilisation ultérieure ou appelez `FMRMSv1MetadataHandler.setUpdatedMetadata()`.