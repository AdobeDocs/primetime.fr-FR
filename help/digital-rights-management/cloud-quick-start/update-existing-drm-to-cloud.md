---
seo-title: Mettre à jour le contenu DRM existant pour utiliser Cloud DRM (facultatif)
title: Mettre à jour le contenu DRM existant pour utiliser Cloud DRM (facultatif)
uuid: cfabeb06-210f-45af-b8a6-8e0b03a76103
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Mettre à jour le contenu DRM existant pour utiliser Cloud DRM (facultatif) {#update-existing-drm-content-to-use-cloud-drm-optional}

Si vous disposez d’une bibliothèque de contenu existante protégée par le DRM Primetime, il est possible de &quot;renommer&quot; le contenu existant pour utiliser le service DRM de Primetime Cloud, au lieu d’avoir à recompresser/chiffrer les fichiers source d’origine. Le fait de renommer le contenu met simplement à jour les métadonnées DRM du contenu dans le manifeste HLS. Il n’effectue aucun déchiffrement/re-chiffrement de la ressource d’origine. Il peut s’agir d’une option utile si le contenu source d’origine n’est pas disponible ou si la quantité de ressources nécessaires pour recompresser une grande bibliothèque suscite des inquiétudes.

Il est possible d’utiliser le SDK Java DRM de Primetime pour mettre à jour les métadonnées par programmation. En outre, l&#39;outil de ligne de [!DNL OfflinePackager.jar] commande inclus dans ce kit de protection peut également effectuer cette tâche à l&#39;aide de l&#39; `-drm_refresh` option.

## Détails du nouvel en-tête {#section_3F3980D8E775450588C64E02A8448189}

La nouvelle en-tête doit mettre à jour les champs suivants pour utiliser CloudDRM :

* URL du serveur de licences (vers [!DNL ht<span></span>tps://access.adobeprimetime.com/flashaccessserver/axs_prod])
* Certificat du serveur de licences (au certificat du serveur de licences CloudDRM)
* Certificat de transport (vers le certificat de transport CloudDRM)
* Informations d’identification de Packager (aux informations d’identification de Packager que vous avez activées pour une utilisation avec CloudDRM)

## Recherche des métadonnées DRM {#section_28721CB7966F40708AEC8637F2E9BB72}

Le contenu qui utilise la technologie HTTP (HDS ou HLS, par exemple) utilise un manifeste qui référence les métadonnées DRM d’Adobe Access. Dans HDS, les métadonnées sont référencées par la `<drmmeta>` balise et dans HLS, elles sont référencées par la `#EXT-X-FAXS-CM` balise. Dans les deux cas, les métadonnées peuvent être contenues en ligne dans le manifeste sous la forme d’un blob codé en base 64 ou référencées en externe sous la forme d’un fichier binaire. Si les métadonnées sont incorporées/insérées dans le manifeste, vous devrez peut-être tout d’abord décoder les métadonnées en données binaires avant d’utiliser ces données pour instancier les métadonnées DRM.

## Utilisation du fichier OfflinePacakger.jar inclus {#section_37C2091856E44AA380D742C72B4DD1A7}

Fournissez le fichier `-drm_refresh option` à la ligne de commande. Un nouveau fichier manifeste sera créé avec les métadonnées DRM mises à jour, tandis que le contenu ne sera pas re-chiffré.

## Utilisation du SDK Java DRM de Primetime pour réen-tête {#section_7EDBAC4C78DF4CD5BE8410EEAD8437A2}

La mise à jour d’une Métadonnées DRM existante peut être réalisée à l’aide du SDK Java DRM Primetime (anciennement appelé Adobe Access DRM) pour une approche par programmation. Pour plus d’informations, reportez-vous à l’exemple de [!DNL RegenerateMetadata.java] code dans le [!DNL /Reference Implmentation/Command Line Tools/samples/] package du SDK. Le SDK Java d’Adobe Access ne fait pas partie de ce kit de protection CloudDRM et doit être acquis directement auprès d’Adobe. Pour plus d’informations, contactez votre représentant commercial Adobe.