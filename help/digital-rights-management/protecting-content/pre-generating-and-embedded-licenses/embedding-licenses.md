---
title: Incorporation de licences
description: Incorporation de licences
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Incorporation de licences {#embedding-licenses}

Une fois que le contenu a été chiffré et qu’une licence a été prégénérée, la licence peut être incorporée au contenu chiffré.

Si vous souhaitez incorporer une licence, vous devez obtenir une instance de `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Si vous connaissez le type de contenu chiffré, utilisez le constructeur pour `FLVKeyMetaDataUpdater` ou `F4VKeyMetaDataUpdater`; sinon, utilisez `MediaProcessorFactory.getMediaProcessor()` pour renvoyer une instance en fonction du type de fichier détecté. Ensuite, vous devez construire `KeyMetaDataCallback` et appeler `modifyKeyMetaData()`. Votre mise en oeuvre de rappel est ensuite appelée lorsque les métadonnées DRM se trouvent dans le contenu chiffré. Selon les métadonnées trouvées, vous pouvez choisir une licence à incorporer et définir la licence à l’aide de `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

Voir `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` dans le répertoire Reference Implementation Command Line Tools [!DNL Samples] pour obtenir un exemple de code qui illustre les licences incorporées.

>[!NOTE]
>
>Un client Adobe Primetime DRM 2.0 ignore toutes les licences incorporées dans le contenu, puis tente d’obtenir une licence du serveur de licences spécifiée dans les métadonnées. Cependant, si les métadonnées indiquent qu’aucun serveur de licences n’est disponible, un client DRM 2.0 Primetime doit être mis à niveau avant de pouvoir vue le contenu.

