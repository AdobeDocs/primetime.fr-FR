---
seo-title: Incorporation de licences
title: Incorporation de licences
uuid: e3d55376-07de-479c-9a53-04bc8071ced4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Incorporation de licences {#embedding-licenses}

Une fois que le contenu a été chiffré et qu’une licence a été prégénérée, la licence peut être incorporée au contenu chiffré.

Si vous souhaitez incorporer une licence, vous devez obtenir une instance de `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Si vous connaissez le type de contenu chiffré, utilisez le constructeur pour `FLVKeyMetaDataUpdater` ou `F4VKeyMetaDataUpdater`; sinon, utilisez `MediaProcessorFactory.getMediaProcessor()` pour renvoyer une instance en fonction du type de fichier détecté. Ensuite, vous devez construire un `KeyMetaDataCallback` et appeler `modifyKeyMetaData()`. Votre mise en oeuvre de rappel est ensuite appelée lorsque les métadonnées DRM se trouvent dans le contenu chiffré. En fonction des métadonnées trouvées, vous pouvez choisir une licence à incorporer et définir la licence à l’aide de `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

Consultez `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` le répertoire Reference Implementation Command Line Tools [!DNL Samples] pour obtenir un exemple de code qui illustre les licences incorporées.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Un client Adobe Primetime DRM 2.0 ignore toutes les licences incorporées dans le contenu, puis tente d’obtenir une licence du serveur de licences spécifiée dans les métadonnées. Cependant, si les métadonnées indiquent qu’aucun serveur de licences n’est disponible, un client DRM 2.0 Primetime doit être mis à niveau avant de pouvoir vue le contenu.

