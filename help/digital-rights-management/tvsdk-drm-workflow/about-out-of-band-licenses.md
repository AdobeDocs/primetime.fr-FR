---
seo-title: Présentation des licences hors bande
title: Présentation des licences hors bande
uuid: 82e4529a-ee1b-4c0c-8885-e0e68319d1a0
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Licences hors bande {#out-of-band-licenses}

Les licences peuvent également être obtenues hors bande (sans contacter un serveur de licences DRM Primetime) en stockant la licence sur disque et en mémoire à l’aide de la `storeVoucher()` méthode.

Pour lire des vidéos chiffrées dans Primetime, le runtime correspondant doit obtenir la licence pour cette vidéo. La licence contient la clé de déchiffrement de la vidéo et est générée par le serveur de licences DRM Primetime que le client a déployé.

Le runtime obtient généralement cette licence en envoyant une demande de licence au serveur de licences DRM Primetime indiqué dans les métadonnées DRM de la vidéo ( `DRMContentData` classe). L’application peut déclencher cette demande de licence en appelant la `DRMManager.loadVoucher()` méthode.

`DRMManager.storeVoucher()` permet à l’application d’envoyer des licences obtenues hors bande. Le moteur d’exécution peut alors ignorer le processus de demande de licence et utiliser les licences transférées pour lire des vidéos chiffrées. La licence doit encore être générée par le serveur de licences DRM Primetime avant d’être obtenue hors bande. Cependant, vous avez la possibilité d’héberger les licences sur n’importe quel serveur HTTP, au lieu d’un serveur de licences DRM Primetime.

`DRMManager.storeVoucher()` est également utilisée pour prendre en charge le partage de licences entre plusieurs périphériques. Après Primetime DRM 3.0, cette fonctionnalité est appelée &quot;Prise en charge du domaine de périphérique&quot;. Si votre déploiement prend en charge ce cas d’utilisation, vous pouvez enregistrer plusieurs ordinateurs dans un groupe de périphériques à l’aide de la `DRMManager.addToDeviceGroup()` méthode. S’il existe un ordinateur doté d’une licence liée au domaine valide pour un contenu donné, l’application peut alors extraire la licence sérialisée à l’aide de la `DRMVoucher.toByteArray()` méthode et sur vos autres ordinateurs, vous pouvez importer les licences à l’aide de la `DRMManager.storeVoucher()` méthode.

## A propos de l’enregistrement de périphérique {#about-device-registration}

Toutes les licences DRM Primetime, au moment de la création, doivent être liées à une entité finale. La liaison est le processus cryptographique qui consiste à autoriser uniquement une entité spécifique à consommer la licence. Cela est nécessaire pour empêcher les &quot;licences flottantes&quot; qui peuvent être utilisées par n&#39;importe quel appareil arbitraire. Pour que Primetime DRM puisse &quot;pré-générer&quot; des licences, cela signifie que le &quot;&quot; de ces licences pré-générées doit être connu à l’avance. Primetime DRM appelle cela &quot;Enregistrement de périphérique&quot;.

## Enregistrement d’un périphérique {#register-a-device}

Supposons que vous ayez effectué le  suivant :

* Vous avez configuré le SDK de serveur DRM Primetime.
* Vous avez configuré un serveur HTTP pour émettre des licences pré-générées.
* Vous avez créé une application Primetime pour le contenu protégé.

 La phase d’enregistrement des périphériques implique les actions suivantes :

1. L’application crée un identifiant généré de manière aléatoire.
1. L’application appelle la `DRMManager.authenticate()` méthode. L’application doit inclure l’identifiant généré de manière aléatoire dans la demande d’authentification. Par exemple, incluez l’ID dans le champ username.
1. L’action mentionnée à l’étape 2 entraînera l’envoi par DRM Primetime d’une demande d’authentification au serveur du client. Cette demande inclut le certificat du périphérique :
   1. Le serveur extrait le certificat du périphérique et l’ID généré de la requête et les stocke.
   1. Le sous-système client génère automatiquement des licences pour ce certificat de périphérique, les stocke et leur accorde l’accès de manière à les associer à l’identifiant généré. .
1. Le serveur répond à la demande par un message de réussite.
1. L’application stocke l’ID généré.

Après l’enregistrement du périphérique, l’application utilise l’ID généré de la même manière qu’elle aurait utilisé l’ID du périphérique dans le schéma précédent :
1. L’application tente de localiser l’identifiant généré.
1. Si l’ID généré est trouvé, l’application utilise l’ID généré lors du téléchargement des licences prégénérées. L’application enverra les licences au client DRM Primetime pour consommation à l’aide de la `DRMManager.storeVoucher()` méthode. .
1. Si l’ID généré est introuvable, l’application passe par la procédure d’enregistrement du périphérique.

## Réinitialisation en usine DRM {#drm-factory-reset}

Lorsque l’utilisateur du périphérique appelle l’option de réinitialisation en usine DRM, le certificat du périphérique est purgé. Pour continuer la lecture du contenu protégé, l’application doit à nouveau passer par la procédure d’enregistrement du périphérique. Si l’application envoie une licence pré-générée obsolète, le client DRM Primetime la rejette, car la licence a été chiffrée pour un ancien ID de périphérique.

* API Flash : [DRMManager.resetDRMVouchers()](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMManager.html#resetDRMVouchers()) - (Peut uniquement être appelé en réponse à certains codes d’erreur DRM non récupérables.)
* API iOS : [DRMManager resetDRM](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a0dd6c9662428583196e0419d3ea69446)
* API Android : [DRMManager.resetDRM()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#resetDRM(com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))