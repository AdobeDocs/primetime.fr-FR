---
description: En règle générale, toutes les licences DRM Primetime, au moment de la création, sont liées à un appareil unique. Cette liaison empêche les utilisateurs de partager des licences sur différents appareils sans autorisation. En plus de la liaison par appareil, Primetime DRM permet de lier des licences à un domaine d’appareil ou à un groupe d’appareils.
title: Lire du contenu chiffré à l’aide de la prise en charge des domaines
exl-id: 3c9badfc-046b-4c56-bde1-7b3b708bfaa2
source-git-commit: 59f7f8aa82be59c4012ee80648032600590bc4e1
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Prise en charge des domaines d’appareil {#device-domain-support}

En règle générale, toutes les licences DRM Primetime, au moment de la création, sont liées à un appareil unique. Cette liaison empêche les utilisateurs de partager des licences sur différents appareils sans autorisation. En plus de la liaison par appareil, Primetime DRM permet de lier des licences à un domaine d’appareil ou à un groupe d’appareils.

Si les métadonnées de contenu spécifient que l’enregistrement du domaine de l’appareil est requis, l’application peut appeler une API pour rejoindre un groupe d’appareils. Cette action déclenche l’envoi d’une demande d’enregistrement de domaine au serveur de domaine. Une fois qu’une licence est émise à un groupe d’appareils, celle-ci peut être exportée et partagée avec d’autres appareils qui ont rejoint le groupe d’appareils.

Les informations du groupe d’appareils sont ensuite utilisées dans l’objet `DRMContentData` `VoucherAccessInfo`, qui sera ensuite utilisé pour présenter les informations requises pour récupérer et utiliser une licence.

## Lire du contenu chiffré à l’aide de la prise en charge des domaines {#play-encrypted-content-using-domain-support}

Pour lire du contenu chiffré à l’aide de Primetime DRM , procédez comme suit :

1. À l’aide de `VoucherAccessInfo.deviceGroup`, vérifiez si l’enregistrement du groupe d’appareils est requis.
1. Si l’authentification est requise :
   1. Utilisez la propriété `DeviceGroupInfo.authenticationMethod` pour savoir si l’authentification est requise.
   1. Si une authentification est requise, authentifiez l’utilisateur en effectuant l’une des étapes suivantes :

      * Obtenez le nom d’utilisateur et le mot de passe de l’utilisateur et appelez `DRMManager.authenticate(deviceGroup.serverURL, deviceGroup.domain, username, password)`.
      * Obtenez un jeton d’authentification mis en cache/prégénéré et appelez `DRMManager.setAuthenticationToken()`.
   1. Appeler `DRMManager.addToDeviceGroup()`
1. Obtenez la licence du contenu en effectuant l’une des tâches suivantes :
   1. Utilisez la méthode `DRMManager.loadVoucher()` .
   1. Obtenez la licence à partir d’un appareil différent enregistré dans le même groupe d’appareils et fournissez la licence à `DRMManager` par l’intermédiaire de la méthode `DRMManager.storeVoucher()`.
1. Lire le contenu chiffré à l’aide de la méthode `Primetime.play()`.
Pour exporter la licence du contenu, n’importe quel appareil peut fournir les octets bruts de la licence à l’aide de la méthode `DRMVoucher.toByteArray()` après avoir obtenu la licence du serveur de licences DRM Primetime. Les fournisseurs de contenu limitent généralement le nombre d’appareils d’un groupe. Si la limite est atteinte, vous devrez peut-être appeler la méthode `DRMManager.removeFromDeviceGroup()` sur un appareil inutilisé avant d’enregistrer l’appareil actuel.
