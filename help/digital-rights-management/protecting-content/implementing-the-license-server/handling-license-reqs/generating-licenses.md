---
title: Génération de licences
description: Génération de licences
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---


# Génération de licences{#generating-licenses}

Si vous souhaitez délivrer une licence feuille à un utilisateur, le SDK doit déchiffrer le CEK contenu dans les métadonnées de contenu et le chiffrer à nouveau pour l’ordinateur qui demande une licence. Pour déchiffrer le CEK, le serveur doit fournir les informations requises pour déchiffrer la clé. Appelez `ContentInfo.setKeyRetrievalInfo()` et fournissez un objet `AsymmetricKeyRetrieval`. Si les métadonnées comportent plusieurs stratégies, le serveur doit déterminer la stratégie à utiliser et appeler `LicenseRequestMessage.setSelectedPolicy()`. Ensuite, appelez `LicenseRequestMessage.generateLicense()` pour générer la licence. En utilisant l&#39;objet `License` renvoyé, vous pouvez modifier l&#39;expiration ou les droits de la licence.

Si un objet `ExternalKeyRetrieval` est spécifié dans l&#39;objet `ContentInfo`, le serveur de licences doit alors utiliser l&#39;identifiant CEK associé pour récupérer le CEK approprié qui est inséré dans la licence.

Pour plus d’informations sur l’utilisation du flux de travail CEK externe, voir [Aperçu du CEK externe DRM d’Adobe Primetime](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md).
