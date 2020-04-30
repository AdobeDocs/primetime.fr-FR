---
seo-title: Mise à niveau des métadonnées
title: Mise à niveau des métadonnées
uuid: cad0b23e-50ca-47ae-871f-be571cb00a26
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Mise à niveau des métadonnées{#upgrading-metadata}

Si un client Adobe Access détecte du contenu fourni avec Flash Media Rights Management Server 1.x, il extrait les métadonnées de chiffrement du contenu et les envoie au serveur. Le serveur convertit les métadonnées FMRMS 1.x au format Adobe Access et les renvoie au client. Le client envoie ensuite les métadonnées mises à jour dans une demande de licence Adobe Access standard.

* La classe du gestionnaire de requêtes est `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`.
* L’URL de demande est &quot;URL de *base à partir du contenu* 1.x&quot; +&quot;/flashaccess/headerconversion/v1&quot;.

La conversion des métadonnées peut être effectuée à la volée lorsque le serveur reçoit les anciennes métadonnées du client. Le serveur peut également prétraiter l’ancien contenu et stocker les métadonnées converties ; dans ce cas, lorsque le client demande de nouvelles métadonnées, le serveur doit simplement récupérer les nouvelles métadonnées correspondant à l’identifiant de licence des anciennes métadonnées.

Pour convertir les métadonnées, le serveur doit effectuer les opérations suivantes :

* Allez `LiveCycleKeyMetaData`! Pour préconvertir les métadonnées, `LiveCycleKeyMetaData` vous pouvez vous procurer un fichier compressé de la version 1.x à l’aide `MediaEncrypter.examineEncryptedContent()`. Les métadonnées sont également incluses dans la demande de conversion de métadonnées ( `FMRMSv1MetadataHandler.getOriginalMetadata()`).
* Récupérez l’identifiant de licence à partir des anciennes métadonnées et recherchez la clé de chiffrement et les stratégies (ces informations figuraient à l’origine dans la base de données Adobe LiveCycle ES. Les stratégies LiveCycle ES doivent être converties en stratégies Adobe Access 2.0.) La mise en oeuvre des références comprend des scripts et des exemples de code pour la conversion des stratégies et l’exportation des informations de licence à partir de LiveCycle ES.
* Renseignez l’ `V2KeyParameters` objet (que vous récupérez en appelant `MediaEncrypter.getKeyParameters()`).
* Chargez les informations `SigningCredential`d’identification de packager émises par Adobe pour signer les métadonnées de chiffrement. Obtenez l’ `SignatureParameters` objet en appelant `MediaEncrypter.getSignatureParameters()` et en remplissant les informations d’identification de signature.
* Appelez `MetaDataConverter.convertMetadata()` pour obtenir le `V2ContentMetaData`.
* Appelez `V2ContentMetaData.getBytes()` et stockez pour une utilisation ultérieure, ou appelez `FMRMSv1MetadataHandler.setUpdatedMetadata()`.

