---
description: En règle générale, toutes les licences DRM Primetime, au moment de la création, sont liées à un périphérique unique. Cette liaison empêche les utilisateurs de partager des licences sur différents périphériques sans autorisation. Outre la liaison par périphérique, Primetime DRM permet de lier des licences à un domaine de périphérique ou à un groupe de périphériques.
seo-description: En règle générale, toutes les licences DRM Primetime, au moment de la création, sont liées à un périphérique unique. Cette liaison empêche les utilisateurs de partager des licences sur différents périphériques sans autorisation. Outre la liaison par périphérique, Primetime DRM permet de lier des licences à un domaine de périphérique ou à un groupe de périphériques.
seo-title: Lecture du contenu chiffré à l’aide de la prise en charge des domaines
title: Lecture du contenu chiffré à l’aide de la prise en charge des domaines
uuid: 8854cc0f-9bfc-4833-82d7-a3f46ac88e06
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Prise en charge des domaines de périphérique {#device-domain-support}

En règle générale, toutes les licences DRM Primetime, au moment de la création, sont liées à un périphérique unique. Cette liaison empêche les utilisateurs de partager des licences sur différents périphériques sans autorisation. Outre la liaison par périphérique, Primetime DRM permet de lier des licences à un domaine de périphérique ou à un groupe de périphériques.

Si les métadonnées de contenu indiquent que l’enregistrement du domaine de l’appareil est requis, l’application peut appeler une API pour rejoindre un groupe d’appareils. Cette action déclenche l’envoi d’une demande d’enregistrement de domaine au serveur de domaine. Une fois qu’une licence est délivrée à un groupe de périphériques, celle-ci peut être exportée et partagée avec d’autres périphériques qui ont rejoint ce groupe.

Les informations du groupe de périphériques sont ensuite utilisées dans l’ `DRMContentData` objet `VoucherAccessInfo` , qui sera ensuite utilisé pour présenter les informations requises pour récupérer et utiliser une licence.

## Lecture du contenu chiffré à l’aide de la prise en charge des domaines {#play-encrypted-content-using-domain-support}

Pour lire du contenu chiffré à l’aide de Primetime DRM, procédez comme suit :

1. A l’aide `VoucherAccessInfo.deviceGroup`, vérifiez si l’enregistrement du groupe de périphériques est requis.
1. Si l&#39;authentification est requise :
   1. Utilisez la `DeviceGroupInfo.authenticationMethod` propriété pour savoir si une authentification est requise.
   1. Si l’authentification est requise, authentifiez l’utilisateur en procédant de l’UNE des manières suivantes :

      * Récupérez le nom d’utilisateur et le mot de passe de l’utilisateur et appelez `DRMManager.authenticate(deviceGroup.serverURL, deviceGroup.domain, username, password)`.
      * Procurez-vous un jeton d’authentification mis en cache/pré-généré et appelez `DRMManager.setAuthenticationToken()`.
   1. Appeler `DRMManager.addToDeviceGroup()`
1. Obtenez la licence du contenu en exécutant l’une des tâches suivantes :
   1. Utilisez la `DRMManager.loadVoucher()` méthode.
   1. Récupérez la licence d’un périphérique différent enregistré dans le même groupe de périphériques et fournissez la licence à l’utilisateur ` DRMManager` par le biais de la `DRMManager.storeVoucher()` méthode.
1. Lisez le contenu chiffré à l’aide de la `Primetime.play()` méthode.
Pour exporter la licence du contenu, n’importe quel périphérique peut fournir les octets bruts de la licence en utilisant la `DRMVoucher.toByteArray()` méthode après avoir obtenu la licence auprès du serveur de licences DRM Primetime. Les fournisseurs de contenu limitent généralement le nombre de périphériques d’un groupe de périphériques. Si la limite est atteinte, vous devrez peut-être appeler la `DRMManager.removeFromDeviceGroup()` méthode sur un périphérique inutilisé avant d&#39;enregistrer le périphérique actuel.