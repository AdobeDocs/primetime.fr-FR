---
title: Mise à niveau des métadonnées
description: Mise à niveau des métadonnées
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Mise à niveau des métadonnées{#upgrading-metadata}

Si un client Adobe Access rencontre du contenu compressé avec le serveur Flash Media Rights Management 1.x, il extrait les métadonnées de chiffrement du contenu et les envoie au serveur. Le serveur convertit les métadonnées FMRMS 1.x au format Adobe Access et les renvoie au client. Le client envoie ensuite les métadonnées mises à jour dans une demande de licence d’accès Adobe standard.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`.
* L’URL de demande est &quot;*URL de base du contenu 1.x*&quot; +&quot;/flashaccess/headerconversion/v1&quot;.

La conversion des métadonnées peut être effectuée instantanément lorsque le serveur reçoit les anciennes métadonnées du client. Le serveur peut également prétraiter l’ancien contenu et stocker les métadonnées converties. Dans ce cas, lorsque le client demande de nouvelles métadonnées, le serveur doit simplement récupérer les nouvelles métadonnées correspondant à l’identifiant de licence des anciennes métadonnées.

Pour convertir les métadonnées, le serveur doit effectuer les étapes suivantes :

* Get `LiveCycleKeyMetaData`. Pour préconvertir les métadonnées, `LiveCycleKeyMetaData` peut être obtenu à partir d’un fichier empaqueté 1.x à l’aide de `MediaEncrypter.examineEncryptedContent()`. Les métadonnées sont également incluses dans la requête de conversion de métadonnées ( `FMRMSv1MetadataHandler.getOriginalMetadata()`).
* Récupérez l’identifiant de licence à partir des anciennes métadonnées et recherchez la clé de chiffrement et les stratégies (ces informations figuraient à l’origine dans la base de données Adobe LiveCycle ES. Les stratégies ES de LiveCycle doivent être converties en stratégies d’accès Adobe 2.0.) La mise en oeuvre de référence comprend des scripts et un exemple de code pour la conversion des stratégies et l’exportation des informations de licence à partir de LiveCycle ES.
* Renseignez les `V2KeyParameters` (que vous récupérez en appelant `MediaEncrypter.getKeyParameters()`).
* Chargez la variable `SigningCredential`, qui est les informations d’identification de packager émises par l’Adobe utilisé pour signer les métadonnées de chiffrement. Obtenez la variable `SignatureParameters` en appelant `MediaEncrypter.getSignatureParameters()` et renseignez les informations d’identification de signature.
* Appeler `MetaDataConverter.convertMetadata()` pour obtenir la variable `V2ContentMetaData`.
* Appeler `V2ContentMetaData.getBytes()` et stocker pour une utilisation ultérieure ou appeler `FMRMSv1MetadataHandler.setUpdatedMetadata()`.
