---
seo-title: Incorporation de licences
title: Incorporation de licences
uuid: b8d8ee9b-7430-4899-9caf-47d6b64021b8
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Incorporation de licences {#embedding-licenses}

Une fois que le contenu a été chiffré et qu’une licence a été prégénérée, la licence peut être incorporée au contenu chiffré.

Pour incorporer une licence, obtenez une instance de `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Si vous connaissez le type de contenu chiffré, utilisez le constructeur pour `FLVKeyMetaDataUpdater` ou `F4VKeyMetaDataUpdater`; sinon, utilisez `MediaProcessorFactory.getMediaProcessor()` pour renvoyer une instance en fonction du type de fichier détecté. Créez un `KeyMetaDataCallback` et appelez `modifyKeyMetaData()`. Votre mise en oeuvre de rappel sera appelée lorsque les métadonnées DRM se trouvent dans le contenu chiffré. Selon les métadonnées trouvées, vous pouvez choisir une licence à incorporer et définir la licence à l’aide de `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

Pour obtenir un exemple de code démontrant les licences incorporées, voir `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` dans le répertoire Reference Implementation Command Line Tools &quot;Samples&quot;.

>[!NOTE]
>
>Les clients d&#39;Adobe Access 2.0 ignoreront toutes les licences incorporées dans le contenu et tenteront d&#39;obtenir une licence auprès du serveur de licences spécifié dans les métadonnées. Toutefois, si les métadonnées indiquent qu’aucun serveur de licences n’est disponible, un client Adobe Access 2.0 devra effectuer la mise à niveau vers la vue du contenu.

Voir [Licences hors bande](../../aaxs-protecting-content/content-introduction/packaging-options/content-out-of-band-licenses.md).
