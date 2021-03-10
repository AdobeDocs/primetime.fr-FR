---
title: Incorporation de licences
description: Incorporation de licences
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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
