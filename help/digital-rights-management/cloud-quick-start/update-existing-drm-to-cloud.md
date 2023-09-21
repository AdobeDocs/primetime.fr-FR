---
title: Mettre à jour le contenu DRM existant pour utiliser Cloud DRM (facultatif)
description: Mettre à jour le contenu DRM existant pour utiliser Cloud DRM (facultatif)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Mettre à jour le contenu DRM existant pour utiliser Cloud DRM (facultatif) {#update-existing-drm-content-to-use-cloud-drm-optional}

Si vous disposez d’une bibliothèque de contenu existante protégée par Primetime DRM, il est possible de &quot;recompresser&quot; le contenu existant pour utiliser le service DRM de Primetime Cloud, au lieu d’avoir à recompresser/chiffrer les fichiers source originaux. Le fait de renommer le contenu met simplement à jour les métadonnées DRM du contenu dans le manifeste HLS. Il n’effectue aucun déchiffrement/re-chiffrement de la ressource d’origine. Il peut s’agir d’une option utile si le contenu source d’origine n’est pas disponible ou si la quantité de ressources requises pour recompresser une grande bibliothèque suscite des inquiétudes.

Il est possible d’utiliser le SDK Java DRM Primetime pour mettre à jour les métadonnées par programmation. En outre, la variable [!DNL OfflinePackager.jar] L’outil de ligne de commande inclus dans ce kit de protection peut également réaliser cette tâche à l’aide de la fonction `-drm_refresh` .

## Détails du réen-tête {#section_3F3980D8E775450588C64E02A8448189}

Le ré-entête doit mettre à jour les champs suivants pour utiliser CloudDRM :

* URL du serveur de licences (à [!DNL ht<span></span>tps://access.adobeprimetime.com/flashaccessserver/axs_prod])
* Certificat du serveur de licences (certificat du serveur de licences CloudDRM)
* Certificat de transport (au certificat de transport CloudDRM)
* Informations d’identification de Packager (aux informations d’identification de packager que vous avez activées pour une utilisation avec CloudDRM)

## Recherche des métadonnées DRM {#section_28721CB7966F40708AEC8637F2E9BB72}

Le contenu qui utilise la technologie HTTP (comme HDS ou HLS) utilise un manifeste qui référence les métadonnées DRM d’accès Adobe. Dans HDS, les métadonnées sont référencées par le `<drmmeta>` et dans HLS, il est référencé par la balise `#EXT-X-FAXS-CM` balise . Dans les deux scénarios, les métadonnées peuvent être contenues en ligne dans le manifeste sous la forme d’un objet blob codé en base 64 ou référencées en externe sous la forme d’un fichier binaire. Si les métadonnées sont incorporées/insérées dans le manifeste, vous devrez peut-être tout d’abord décoder les métadonnées en données binaires avant d’utiliser ces données pour instancier les métadonnées DRM.

## Utilisation du fichier OfflinePack.jar inclus {#section_37C2091856E44AA380D742C72B4DD1A7}

Apportez la variable `-drm_refresh option` à la ligne de commande. Un nouveau fichier de manifeste sera créé avec les métadonnées DRM mises à jour, tandis que le contenu ne sera pas chiffré à nouveau.

## Utilisation du SDK Java DRM Primetime pour réinitialiser le titre {#section_7EDBAC4C78DF4CD5BE8410EEAD8437A2}

La mise à jour d’une métadonnées DRM existante peut être effectuée à l’aide du SDK Java Primetime DRM (anciennement appelé Adobe Access DRM) pour une approche programmatique. Pour plus d’informations, reportez-vous au [!DNL RegenerateMetadata.java] exemple de code dans le [!DNL /Reference Implmentation/Command Line Tools/samples/] du SDK. Le SDK Java Adobe Access ne fait pas partie de ce CloudDRM Protection Kit et doit être acquis directement à partir d’Adobe. Pour plus d’informations, contactez votre contact pour affaires Adobe.
