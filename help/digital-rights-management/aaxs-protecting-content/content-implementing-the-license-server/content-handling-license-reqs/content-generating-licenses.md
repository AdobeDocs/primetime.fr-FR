---
title: Génération de licences
description: Génération de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Génération de licences {#generating-licenses}

Pour délivrer une licence feuille à l’utilisateur, le SDK doit déchiffrer le CEK contenu dans les métadonnées de contenu et le chiffrer à nouveau pour la machine qui demande une licence. Pour déchiffrer le CEK, le serveur doit fournir les informations nécessaires pour déchiffrer la clé. Appeler `ContentInfo.setKeyRetrievalInfo()` et de fournir un `AsymmetricKeyRetrieval` . Si les métadonnées contiennent plusieurs stratégies, le serveur doit déterminer la stratégie à utiliser et à appeler. `LicenseRequestMessage.setSelectedPolicy()`. Alors appelez `LicenseRequestMessage.generateLicense()` pour générer la licence. En utilisant la variable `License` , vous pouvez modifier l’expiration ou les droits contenus dans la licence.

Si un objet ExternalKeyRetrieval est spécifié dans la variable `ContentInfo` , alors le serveur de licences doit utiliser l’identifiant CEK associé pour récupérer le CEK approprié qui sera inséré dans la licence. Pour plus d’informations sur l’utilisation du workflow de CEK externe, voir [Présentation du CEK externe Adobe Access DRM](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)
