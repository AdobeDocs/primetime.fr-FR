---
title: Incorporation de licences
description: Incorporation de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Incorporation de licences {#embedding-licenses}

Une fois le contenu chiffré et une licence pré-générée, la licence peut être incorporée dans le contenu chiffré.

Si vous souhaitez incorporer une licence, vous devez obtenir une instance de `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Si vous connaissez le type de contenu chiffré, utilisez le constructeur pour `FLVKeyMetaDataUpdater` ou `F4VKeyMetaDataUpdater`; sinon, utilisez `MediaProcessorFactory.getMediaProcessor()` pour renvoyer une instance en fonction du type de fichier détecté. Vous devez ensuite construire une `KeyMetaDataCallback` et invoke `modifyKeyMetaData()`. Votre mise en oeuvre de rappel est ensuite appelée lorsque les métadonnées DRM se trouvent dans le contenu chiffré. En fonction des métadonnées trouvées, vous pouvez choisir une licence à incorporer et définir la licence à l’aide de `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

Voir `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` dans les outils de ligne de commande de mise en oeuvre de référence [!DNL Samples] répertoire pour un exemple de code qui illustre les licences incorporées.

>[!NOTE]
>
>Un client Adobe Primetime DRM 2.0 ignore les licences qui sont incorporées dans le contenu, puis tente d’obtenir une licence du serveur de licences spécifié dans les métadonnées. Cependant, si les métadonnées indiquent qu’aucun serveur de licences n’est disponible, un client Primetime DRM 2.0 doit être mis à niveau avant de pouvoir afficher le contenu.
