---
title: Mise à niveau des métadonnées
description: Mise à niveau des métadonnées
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---


# Mise à niveau des métadonnées{#upgrading-metadata}

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

