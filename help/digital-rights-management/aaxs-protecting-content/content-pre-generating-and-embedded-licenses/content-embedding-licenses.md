---
seo-title: Incorporation de licences
title: Incorporation de licences
uuid: b8d8ee9b-7430-4899-9caf-47d6b64021b8
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Incorporation de licences {#embedding-licenses}

Une fois que le contenu a été chiffré et qu’une licence a été prégénérée, la licence peut être incorporée au contenu chiffré.

Pour incorporer une licence, obtenez une instance de `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Si vous connaissez le type de contenu chiffré, utilisez le constructeur pour `FLVKeyMetaDataUpdater` ou `F4VKeyMetaDataUpdater`; sinon, utilisez `MediaProcessorFactory.getMediaProcessor()` pour renvoyer une instance en fonction du type de fichier détecté. Créez un `KeyMetaDataCallback` et appelez `modifyKeyMetaData()`. Votre mise en oeuvre de rappel sera appelée lorsque les métadonnées DRM se trouvent dans le contenu chiffré. En fonction des métadonnées trouvées, vous pouvez choisir une licence à incorporer et définir la licence à l’aide de `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

Pour obtenir un exemple de code démontrant les licences incorporées, reportez-vous `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` au répertoire &quot;Exemples&quot; des outils de ligne de commande de mise en oeuvre de référence.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Les clients Adobe Access 2.0 ignorent toutes les licences incorporées dans le contenu et tentent d’obtenir une licence auprès du serveur de licences spécifié dans les métadonnées. Toutefois, si les métadonnées indiquent qu’aucun serveur de licences n’est disponible, un client Adobe Access 2.0 devra effectuer la mise à niveau vers la vue du contenu.

Voir Licences [](../../aaxs-protecting-content/content-introduction/packaging-options/content-out-of-band-licenses.md)hors bande.
