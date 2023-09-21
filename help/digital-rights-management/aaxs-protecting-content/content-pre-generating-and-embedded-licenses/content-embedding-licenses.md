---
title: Incorporation de licences
description: Incorporation de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Incorporation de licences {#embedding-licenses}

Une fois le contenu chiffré et une licence pré-générée, la licence peut être incorporée dans le contenu chiffré.

Pour incorporer une licence, obtenez une instance de `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Si vous connaissez le type de contenu chiffré, utilisez le constructeur pour `FLVKeyMetaDataUpdater` ou `F4VKeyMetaDataUpdater`; sinon, utilisez `MediaProcessorFactory.getMediaProcessor()` pour renvoyer une instance en fonction du type de fichier détecté. Créez un `KeyMetaDataCallback` et invoke `modifyKeyMetaData()`. Votre mise en oeuvre de rappel sera appelée lorsque les métadonnées DRM se trouvent dans le contenu chiffré. En fonction des métadonnées trouvées, vous pouvez choisir une licence à incorporer et définir la licence à l’aide de `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

Pour obtenir un exemple de code présentant les licences incorporées, voir `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` dans le répertoire &quot;Exemples&quot; des outils de ligne de commande de mise en oeuvre de référence.

>[!NOTE]
>
>Les clients Adobe Access 2.0 ignoreront les licences incorporées dans le contenu et tenteront d’obtenir une licence du serveur de licences spécifié dans les métadonnées. Cependant, si les métadonnées indiquent qu’aucun serveur de licences n’est disponible, un client Adobe Access 2.0 devra effectuer une mise à niveau pour afficher le contenu.

Voir [Licences hors bande](../../aaxs-protecting-content/content-introduction/packaging-options/content-out-of-band-licenses.md).
