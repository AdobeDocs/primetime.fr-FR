---
description: Il existe deux types de requêtes liées à la compatibilité de Flash Media Rights Management Server 1.x. Un type de requête est utilisé pour inviter les clients 1.x à effectuer une mise à niveau vers un environnement d’exécution prenant en charge Adobe Primetime DRM 2.0 ou version ultérieure. Une autre est utilisée pour mettre à jour les métadonnées 1.x au format DRM Primetime avant qu’une licence ne puisse être demandée. La prise en charge de ces requêtes n’est requise que si vous avez précédemment déployé un contenu utilisant FMRMS 1.0 ou 1.5.
seo-description: Il existe deux types de requêtes liées à la compatibilité de Flash Media Rights Management Server 1.x. Un type de requête est utilisé pour inviter les clients 1.x à effectuer une mise à niveau vers un environnement d’exécution prenant en charge Adobe Primetime DRM 2.0 ou version ultérieure. Une autre est utilisée pour mettre à jour les métadonnées 1.x au format DRM Primetime avant qu’une licence ne puisse être demandée. La prise en charge de ces requêtes n’est requise que si vous avez précédemment déployé un contenu utilisant FMRMS 1.0 ou 1.5.
seo-title: Gestion de la compatibilité FMRMS
title: Gestion de la compatibilité FMRMS
uuid: c32ee087-2edf-4d11-be36-e2b31f3769de
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Gestion de la compatibilité FMRMS {#handling-fmrms-compatibility}

Il existe deux types de requêtes liées à la compatibilité de Flash Media Rights Management Server 1.x. Un type de requête est utilisé pour inviter les clients 1.x à effectuer une mise à niveau vers un environnement d’exécution prenant en charge Adobe Primetime DRM 2.0 ou version ultérieure. Une autre est utilisée pour mettre à jour les métadonnées 1.x au format DRM Primetime avant qu’une licence ne puisse être demandée. La prise en charge de ces requêtes n’est requise que si vous avez précédemment déployé un contenu utilisant FMRMS 1.0 ou 1.5.

## Mise à niveau des clients {#upgrading-clients}

Si un client FMRMS 1.x contacte un serveur DRM Adobe Primetime, le serveur doit demander au client de procéder à la mise à niveau.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* L’URL de requête est &quot;URL de *base à partir du contenu* 1.x&quot; + &quot; [!DNL /edcws/services/urn:EDCLicenseService]&quot;

   Contrairement aux autres gestionnaires de requêtes Adobe Primetime, ce gestionnaire ne permet pas d’accéder à des informations de requête ni ne nécessite la définition de données de réponse. Créez une instance de la `FMRMSv1RequestHandler`, puis appelez `close()`

## Mise à niveau des métadonnées {#upgrading-metadata}

Si un client DRM Adobe Primetime rencontre du contenu fourni avec Flash Media Rights Management Server 1.x, il extrait les métadonnées de chiffrement du contenu et les envoie au serveur. Le serveur convertit ensuite les métadonnées FMRMS 1.x au format DRM Primetime et les envoie au client. Le client envoie ensuite les métadonnées mises à jour dans une demande de licence DRM Primetime standard.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`.
* L’URL de requête est &quot;URL de *base à partir du contenu* 1.x&quot; +&quot; [!DNL /flashaccess/headerconversion/v1]&quot;.

La conversion des métadonnées peut être effectuée à la volée lorsque le serveur reçoit les anciennes métadonnées du client. Le serveur peut également prétraiter l’ancien contenu et stocker les métadonnées converties ; dans ce cas, lorsque le client demande de nouvelles métadonnées, le serveur doit simplement récupérer les nouvelles métadonnées correspondant à l’identifiant de licence des anciennes métadonnées.

Pour convertir les métadonnées, le serveur doit effectuer les étapes suivantes :

* Allez `LiveCycleKeyMetaData`. Pour préconvertir les métadonnées, `LiveCycleKeyMetaData` vous pouvez vous procurer un fichier compressé 1.x à l’aide `MediaEncrypter.examineEncryptedContent()`. Les métadonnées sont également incluses dans la demande de conversion de métadonnées ( `FMRMSv1MetadataHandler.getOriginalMetadata()`).

* Récupérez l’identifiant de licence à partir des anciennes métadonnées et recherchez la clé de chiffrement et les stratégies DRM (ces informations figuraient à l’origine dans la base de données Adobe LiveCycle ES). Les stratégies DRM de LiveCycle ES doivent être converties en stratégies DRM 2.0 DRM Primetime.) La mise en oeuvre de référence comprend des scripts et un exemple de code pour la conversion des stratégies DRM et l’exportation des informations de licence à partir de LiveCycle ES.
* Renseignez l’ `V2KeyParameters` objet (que vous récupérez en appelant `MediaEncrypter.getKeyParameters()`).

* Chargez les informations `SigningCredential`, c’est-à-dire les informations d’identification du gestionnaire de package émises par Adobe, utilisées pour signer les métadonnées de chiffrement. Récupérez l’ `SignatureParameters` objet en appelant `MediaEncrypter.getSignatureParameters()` et renseignez les informations d’identification de la signature.

* Appelez `MetaDataConverter.convertMetadata()` pour obtenir le `V2ContentMetaData`.

* Appelez `V2ContentMetaData.getBytes()` et stockez-les pour une utilisation ultérieure, ou appelez `FMRMSv1MetadataHandler.setUpdatedMetadata()`.