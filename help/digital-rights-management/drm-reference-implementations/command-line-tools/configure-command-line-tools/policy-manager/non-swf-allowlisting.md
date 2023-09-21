---
title: Liste autorisée des applications non SWF
description: Liste autorisée des applications non SWF
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Liste autorisée des applications non SWF {#non-swf-application-isting}

AIR a été la première plateforme présentant les listes autorisées d’applications et le nom de la propriété que vous utilisez pour liste autorisée des applications non SWF (Adobe AIR, iOS, Android, etc.). conserve son nom original : `policy.allowedAIRApplication.n`. Cela permet la lecture du contenu par toutes les applications non Flashs signées avec un certificat de signature avant la publication. On parle alors de *ID de l’application*. Vous pouvez extraire l’ID de l’application à l’aide du [!DNL AdobePublisherIDUtility.jar] outil. Cette liste autorisée sera appliquée sur tout client prenant en charge Primetime DRM.

L’ID d’application est dérivé de la clé publique du certificat de signature utilisé pour signer une application particulière. Si la clé publique du certificat expire un jour, tous les contenus précédents autorisés à lire uniquement sur les applications signées avec l’ancien certificat ne seront pas lus sur la nouvelle application (signée avec le nouveau certificat).

Si vous disposez d’une bibliothèque de contenu autorisée aux applications qui ont été signées avec un certificat de signature spécifique et que ce certificat expire et qu’un nouveau certificat vous est délivré (avec une paire de clés publique/privée différente), votre ancien contenu ne sera pas lu sur votre nouvelle application. *Sauf* vous effectuez l’une des opérations suivantes :

* Utilisez une `PolicyUpdateList` sur votre serveur de licences pour remplacer la stratégie entrante et insérer une nouvelle entrée de Liste autorisée d’application avec le nouveau résumé du certificat de signature.
* Mettez à jour la logique de votre serveur de licences pour remplacer la stratégie entrante et insérer une nouvelle entrée de Liste autorisée d’application.
* Demandez à l’émetteur de votre certificat de signature de vous envoyer un nouveau certificat qui utilise la même paire de clés publique/privée que celle utilisée par votre précédent certificat.
* Si vous diffusez du contenu HDS/HLS faisant référence à un point de terminaison d’URL pour récupérer la variable `DRMMetadata`, vous pouvez régénérer la variable `DRMMetadata` (à l’aide du SDK Java DRM Primetime) pour insérer une nouvelle stratégie DRM contenant une entrée de Liste autorisée d’application mise à jour.

* Recompressez tout votre ancien contenu avec une nouvelle stratégie DRM contenant le résumé de votre nouveau certificat de signature.

Voir `policy.allowedAIRApplication.n` in *Propriétés de configuration* pour plus d’informations.

>[!NOTE]
>
>L’ajout à la liste autorisée d’une application iOS nécessite une approche spéciale. Voir [Liste autorisée de votre application iOS](../../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-allowlist-your-ios-application.md) dans le *Guide du programmeur TVSDK pour iOS*.
