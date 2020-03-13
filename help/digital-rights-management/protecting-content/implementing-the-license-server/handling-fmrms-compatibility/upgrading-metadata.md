---
seo-title: Mise à niveau des métadonnées
title: Mise à niveau des métadonnées
uuid: 769483e6-a2d1-46cb-afcf-557aa807037c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Mise à niveau des métadonnées{#upgrading-metadata}

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

