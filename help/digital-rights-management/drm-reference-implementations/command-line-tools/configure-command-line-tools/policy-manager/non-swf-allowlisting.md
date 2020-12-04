---
seo-title: Application non SWF Autoriser la mise en vente
title: Application non SWF Autoriser la mise en vente
uuid: d4f93b15-e556-4749-95ab-f7f58b1061d7
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# Application non SWF Autoriser la mise en vente {#non-swf-application-isting}

AIR a été la première plate-forme présentant les applications permettant la création de listes et le nom de la propriété que vous utilisez pour la liste autorisée d’applications non SWF (Adobe AIR, iOS, Android, etc.). conserve son nom d’origine : `policy.allowedAIRApplication.n`. Cela permet la lecture du contenu par toutes les applications non Flashs signées avec un certificat de signature avant la publication. On parle alors de *ID de l&#39;application*. Vous pouvez extraire le ID de l&#39;application à l&#39;aide de l&#39;outil [!DNL AdobePublisherIDUtility.jar]. Cette autorisation d’inscription sera appliquée à tout client prenant en charge la gestion des droits numériques Primetime.

Le ID de l&#39;application est dérivé de la clé publique du certificat de signature utilisé pour signer une application particulière. Si la clé publique du certificat expire un jour, tous les contenus précédents autorisés à lire uniquement sur les applications signées avec l’ancien certificat ne seront pas lus sur la nouvelle application (signée avec le nouveau certificat).

Si vous disposez d’une bibliothèque de contenu autorisée à figurer dans les applications signées avec un certificat de signature particulier et que ce certificat expire et que vous recevez un nouveau certificat (avec une paire de clés publique/privée différente), votre ancien contenu ne sera pas lu sur votre nouvelle application *sauf si* vous effectuez l’une des opérations suivantes :

* Utilisez `PolicyUpdateList` sur votre serveur de licences pour remplacer la stratégie entrante et insérer une nouvelle entrée de Liste autorisée d’application avec le résumé du nouveau certificat de signature.
* Mettez à jour la logique de votre serveur de licences afin de remplacer la stratégie entrante et d’insérer une nouvelle entrée Application Liste autorisée.
* Demandez à l’émetteur du certificat de signature de vous délivrer un nouveau certificat qui utilise la même paire de clés publique/privée que celle utilisée par votre certificat précédent.
* Si vous fournissez du contenu HDS/HLS référençant un point de terminaison d&#39;URL pour récupérer `DRMMetadata`, vous pouvez régénérer le `DRMMetadata` (à l&#39;aide du SDK Java DRM Primetime) pour insérer une nouvelle stratégie DRM contenant une entrée de Liste autorisée d&#39;application mise à jour.

* Recompressez tout votre ancien contenu avec une nouvelle stratégie DRM contenant le résumé de votre nouveau certificat de signature.

Voir `policy.allowedAIRApplication.n` dans *Propriétés de configuration* pour plus de détails.

>[!NOTE]
>
>Pour autoriser la mise en vente d’une application iOS, vous devez suivre une approche spéciale. Voir [Liste autorisée de votre application iOS](../../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-allowlist-your-ios-application.md) dans le *Guide du programmeur iOS TVSDK pour iOS*.
