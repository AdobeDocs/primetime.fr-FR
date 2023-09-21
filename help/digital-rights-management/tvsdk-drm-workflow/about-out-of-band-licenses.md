---
title: Présentation des licences hors bande
description: Présentation des licences hors bande
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Licences hors bande {#out-of-band-licenses}

Les licences peuvent également être obtenues hors bande (sans contacter un serveur de licences DRM Primetime) en stockant la licence sur le disque et en mémoire à l’aide de la fonction `storeVoucher()` .

Pour lire des vidéos chiffrées dans Primetime, le runtime respectif doit obtenir la licence de cette vidéo. La licence contient la clé de décryptage de la vidéo et est générée par le serveur de licences Primetime DRM que le client a déployé.

Le runtime obtient généralement cette licence en envoyant une demande de licence au serveur de licences DRM Primetime indiqué dans les métadonnées DRM de la vidéo ( `DRMContentData` ). L’application peut déclencher cette demande de licence en appelant la fonction `DRMManager.loadVoucher()` .

`DRMManager.storeVoucher()` permet à la demande d’envoyer des licences obtenues hors bande. Le runtime peut ensuite ignorer le processus de demande de licence et utiliser les licences transférées pour lire des vidéos chiffrées. La licence doit toujours être générée par le serveur de licences DRM Primetime avant de pouvoir être obtenue hors-bande. Cependant, vous avez la possibilité d’héberger les licences sur n’importe quel serveur HTTP, au lieu d’un serveur de licences DRM Primetime.

`DRMManager.storeVoucher()` est également utilisé pour prendre en charge le partage de licences entre plusieurs appareils. Après Primetime DRM 3.0, cette fonctionnalité est appelée &quot;prise en charge du domaine de périphérique&quot;. Si votre déploiement prend en charge ce cas d’utilisation, vous pouvez enregistrer plusieurs machines dans un groupe d’appareils à l’aide de la variable `DRMManager.addToDeviceGroup()` . S’il existe un ordinateur avec une licence valide liée au domaine pour un contenu donné, l’application peut alors extraire la licence sérialisée à l’aide de la fonction `DRMVoucher.toByteArray()` et sur vos autres machines, vous pouvez importer les licences à l’aide de la méthode `DRMManager.storeVoucher()` .

## À propos de l’enregistrement des périphériques {#about-device-registration}

Toutes les licences DRM Primetime, au moment de la création, doivent être liées à une entité finale. La liaison est le processus cryptographique qui permet uniquement à une entité spécifique d’utiliser la licence. Cela est nécessaire pour empêcher les &quot;licences flottantes&quot; qui peuvent être utilisées par n&#39;importe quel appareil arbitraire. Pour que Primetime DRM &quot;pré-génère&quot; des licences, cela signifie que la &quot;cible&quot; de ces licences pré-générées doit être connue à l’avance. Primetime DRM appelle cela &quot;Enregistrement de périphérique&quot;.

## Enregistrement d’un périphérique {#register-a-device}

Supposons que vous ayez effectué les tâches suivantes :

* Vous avez configuré le SDK Primetime DRM Server.
* Vous avez configuré un serveur HTTP pour émettre des licences prégénérées.
* Vous avez créé une application Primetime pour afficher le contenu protégé.

 La phase d’enregistrement du périphérique implique les actions suivantes :

1. L’application crée un identifiant généré de manière aléatoire.
1. L’application appelle la variable `DRMManager.authenticate()` . L’application doit inclure l’identifiant généré de manière aléatoire dans la demande d’authentification. Par exemple, incluez l’identifiant dans le champ username .
1. L’action mentionnée à l’étape 2 entraînera l’envoi par Primetime DRM d’une demande d’authentification au serveur du client. Cette demande inclut le certificat de l’appareil :
   1. Le serveur extrait le certificat de l’appareil et l’identifiant généré de la requête et le stocke.
   1. Le sous-système client génère automatiquement des licences pour ce certificat d’appareil, les stocke et leur accorde l’accès de manière à les associer à l’identifiant généré. .
1. Le serveur répond à la demande avec un message &quot;success&quot; (succès).
1. L’application stocke l’identifiant généré.

Après l’enregistrement de l’appareil, l’application utilise l’identifiant généré de la même manière qu’elle aurait utilisé l’identifiant de l’appareil dans le schéma précédent :
1. L’application tente de localiser l’identifiant généré.
1. Si l’identifiant généré est trouvé, l’application utilise l’identifiant généré lors du téléchargement des licences prégénérées. La demande enverra les licences au client DRM Primetime à des fins de consommation à l’aide de la méthode `DRMManager.storeVoucher()` . .
1. Si l’identifiant généré est introuvable, l’application passe par la procédure d’enregistrement du périphérique.

## Réinitialisation de l’usine DRM {#drm-factory-reset}

Lorsque l’utilisateur de l’appareil appelle l’option de réinitialisation d’usine DRM, le certificat de l’appareil est purgé. Pour continuer à lire le contenu protégé, l’application doit recommencer la procédure d’enregistrement du périphérique. Si l’application envoie une licence pré-générée obsolète, le client Primetime DRM la rejettera puisque la licence a été chiffrée pour un identifiant d’appareil plus ancien.

* API FLASH : [DRMManager.resetDRMVouchers()](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMManager.html#resetDRMVouchers()) - (Ne peut être appelé qu’en réponse à certains codes d’erreur DRM non récupérables.)
* API IOS : [DRMManager resetDRM](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a0dd6c9662428583196e0419d3ea69446)
* API Android : [DRMManager.resetDRM()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#resetDRM(com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))
