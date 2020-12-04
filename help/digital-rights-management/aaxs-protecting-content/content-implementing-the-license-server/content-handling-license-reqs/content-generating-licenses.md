---
seo-title: Génération de licences
title: Génération de licences
uuid: 242d5567-f609-4781-a8a6-2f3d78471344
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---


# Génération de licences {#generating-licenses}

Pour délivrer une licence feuille à l’utilisateur, le SDK doit déchiffrer le CEK contenu dans les métadonnées de contenu et le chiffrer à nouveau pour l’ordinateur qui demande une licence. Pour déchiffrer le CEK, le serveur doit fournir les informations requises pour déchiffrer la clé. Appelez `ContentInfo.setKeyRetrievalInfo()` et fournissez un objet `AsymmetricKeyRetrieval`. Si les métadonnées contiennent plusieurs stratégies, le serveur doit déterminer la stratégie à utiliser et appeler `LicenseRequestMessage.setSelectedPolicy()`. Ensuite, appelez `LicenseRequestMessage.generateLicense()` pour générer la licence. En utilisant l&#39;objet `License` renvoyé, vous pouvez modifier l&#39;expiration ou les droits de la licence.

Si un objet ExternalKeyRetrieval est spécifié dans l&#39;objet `ContentInfo`, le serveur de licences doit alors utiliser l&#39;identifiant CEK associé pour récupérer le CEK approprié qui sera inséré dans la licence. Pour plus d&#39;informations sur l&#39;utilisation du processus CEK externe, consultez [Présentation du CEK externe DRM d&#39;accès aux Adobes](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)
