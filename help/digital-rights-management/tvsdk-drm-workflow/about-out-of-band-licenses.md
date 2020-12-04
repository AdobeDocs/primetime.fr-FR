---
seo-title: Présentation des licences hors bande
title: Présentation des licences hors bande
uuid: 82e4529a-ee1b-4c0c-8885-e0e68319d1a0
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---


# Licences hors bande {#out-of-band-licenses}

Les licences peuvent également être obtenues hors bande (sans contacter un serveur de licences DRM Primetime) en stockant la licence sur disque et en mémoire à l&#39;aide de la méthode `storeVoucher()`.

Pour lire des vidéos chiffrées dans Primetime, le runtime respectif doit obtenir la licence pour cette vidéo. La licence contient la clé de déchiffrement de la vidéo et est générée par le serveur de licences DRM Primetime que le client a déployé.

Le runtime obtient généralement cette licence en envoyant une demande de licence au serveur de licences DRM Primetime indiqué dans les métadonnées DRM de la vidéo ( `DRMContentData` classe). L&#39;application peut déclencher cette demande de licence en appelant la méthode `DRMManager.loadVoucher()`.

`DRMManager.storeVoucher()` permet à la demande d&#39;envoyer des licences qu&#39;elle a obtenues hors bande. Le runtime peut ensuite ignorer le processus de demande de licence et utiliser les licences transférées pour lire des vidéos chiffrées. La licence doit encore être générée par le serveur de licences DRM Primetime avant d’être obtenue hors bande. Cependant, vous avez la possibilité d’héberger les licences sur n’importe quel serveur HTTP au lieu d’un serveur de licences DRM Primetime.

`DRMManager.storeVoucher()` est également utilisée pour prendre en charge le partage de licences entre plusieurs périphériques. Après Primetime DRM 3.0, cette fonctionnalité est appelée &quot;Prise en charge des domaines de périphérique&quot;. Si votre déploiement prend en charge ce cas d&#39;utilisation, vous pouvez enregistrer plusieurs machines sur un groupe de périphériques à l&#39;aide de la méthode `DRMManager.addToDeviceGroup()`. S’il existe un ordinateur doté d’une licence liée au domaine valide pour un contenu donné, l’application peut alors extraire la licence sérialisée à l’aide de la méthode `DRMVoucher.toByteArray()` et sur vos autres ordinateurs, vous pouvez importer les licences à l’aide de la méthode `DRMManager.storeVoucher()`.

## À propos de l&#39;enregistrement de périphérique {#about-device-registration}

Toutes les licences DRM Primetime, au moment de la création, doivent être liées à une entité finale. La liaison est le processus cryptographique qui consiste à autoriser uniquement une entité spécifique à consommer la licence. Cela est nécessaire pour empêcher les &quot;licences flottantes&quot; qui peuvent être utilisées par n&#39;importe quel dispositif arbitraire. Pour que Primetime DRM puisse &quot;pré-générer&quot; des licences, cela signifie que la &quot;cible&quot; de ces licences pré-générées doit être connue à l&#39;avance. Primetime DRM appelle cela &quot;Enregistrement de périphérique&quot;.

## Enregistrer un périphérique {#register-a-device}

Supposons que vous ayez effectué les tâches suivantes :

* Vous avez configuré le SDK de serveur DRM Primetime.
* Vous avez configuré un serveur HTTP pour émettre des licences pré-générées.
* Vous avez créé une application Primetime pour vue le contenu protégé.

 La phase d&#39;enregistrement des périphériques implique les actions suivantes :

1. L’application crée un identifiant généré de manière aléatoire.
1. L&#39;application appelle la méthode `DRMManager.authenticate()`. L’application doit inclure l’identifiant généré de manière aléatoire dans la demande d’authentification. Par exemple, incluez l’identifiant dans le champ username.
1. L’action mentionnée à l’étape 2 entraînera l’envoi par DRM Primetime d’une demande d’authentification au serveur du client. Cette demande inclut le certificat de périphérique :
   1. Le serveur extrait le certificat du périphérique et l’identifiant généré de la requête et les stocke.
   1. Le sous-système client génère automatiquement des licences pour ce certificat de périphérique, les stocke et leur accorde l’accès de manière à les associer à l’identifiant généré. .
1. Le serveur répond à la demande par un message de réussite.
1. L’application stocke l’identifiant généré.

Après l’enregistrement du périphérique, l’application utilise l’identifiant généré de la même manière qu’elle aurait utilisé l’identifiant du périphérique dans le schéma précédent :
1. L’application tentera de localiser l’identifiant généré.
1. Si l’identifiant généré est trouvé, l’application utilise l’identifiant généré lors du téléchargement des licences prégénérées. L&#39;application enverra les licences au client DRM Primetime à des fins de consommation à l&#39;aide de la méthode `DRMManager.storeVoucher()`. .
1. Si l&#39;ID généré est introuvable, l&#39;application passe par la procédure d&#39;enregistrement du périphérique.

## Réinitialisation de l&#39;usine DRM {#drm-factory-reset}

Lorsque l’utilisateur du périphérique appelle l’option de réinitialisation en usine DRM, le certificat du périphérique est purgé. Pour continuer la lecture du contenu protégé, l’application doit à nouveau passer par la procédure d’enregistrement du périphérique. Si l’application envoie une licence pré-générée obsolète, le client DRM Primetime la rejette car la licence a été chiffrée pour un ancien ID de périphérique.

* API Flash : [DRMManager.resetDRMVouchers()](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMManager.html#resetDRMVouchers()) - (Ne peut être appelé qu&#39;en réponse à certains codes d&#39;erreur DRM non récupérables.)
* API iOS : [DRMManager resetDRM](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a0dd6c9662428583196e0419d3ea69446)
* API Android : [DRMManager.resetDRM()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#resetDRM(com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))