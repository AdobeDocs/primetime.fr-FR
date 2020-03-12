---
seo-title: Génération de licences
title: Génération de licences
uuid: 242d5567-f609-4781-a8a6-2f3d78471344
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Génération de licences {#generating-licenses}

Pour délivrer une licence feuille à l’utilisateur, le SDK doit déchiffrer le CEK contenu dans les métadonnées de contenu et le chiffrer à nouveau pour l’ordinateur qui demande une licence. Pour déchiffrer le CEK, le serveur doit fournir les informations requises pour déchiffrer la clé. Appelez `ContentInfo.setKeyRetrievalInfo()` et fournissez un `AsymmetricKeyRetrieval` objet. Si les métadonnées contiennent plusieurs stratégies, le serveur doit déterminer la stratégie à utiliser et à appeler `LicenseRequestMessage.setSelectedPolicy()`. Appelez ensuite `LicenseRequestMessage.generateLicense()` pour générer la licence. L’ `License` objet renvoyé permet de modifier l’expiration ou les droits de la licence.

Si un objet ExternalKeyRetrieval est spécifié dans l’ `ContentInfo` objet, le serveur de licences doit alors utiliser l’identifiant CEK associé pour récupérer le CEK approprié qui sera inséré dans la licence. Pour plus d’informations sur l’utilisation du flux de travaux CEK externe, voir Présentation du [kit CEK externe DRM d’Adobe Access.](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)
