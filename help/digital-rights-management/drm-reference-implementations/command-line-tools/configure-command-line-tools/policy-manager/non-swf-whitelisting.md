---
seo-title: Liste blanche des applications non SWF
title: Liste blanche des applications non SWF
uuid: d4f93b15-e556-4749-95ab-f7f58b1061d7
translation-type: tm+mt
source-git-commit: a63768e51c911914a6ba9d884e2587fa34939f9d

---


# Liste blanche des applications non SWF {#non-swf-application-whitelisting}

AIR était la première plate-forme présentant la liste blanche des applications et le nom de la propriété que vous utilisez pour les applications non SWF de liste blanche (Adobe AIR, iOS, Android, etc.). conserve son nom d’origine : `policy.allowedAIRApplication.n`. Cela permet à toutes les applications non Flash qui sont signées avec un certificat de signature avant la publication de lire le contenu. On parle alors de **. Vous pouvez extraire le  à l’aide de l’ [!DNL AdobePublisherIDUtility.jar] outil. Cette liste blanche sera appliquée à tout client qui prend en charge la gestion des droits numériques Primetime.

Le  est dérivé de la clé publique du certificat de signature utilisé pour signer une application particulière. Si la clé publique du certificat expire un jour, alors tout le contenu précédent autorisé à lire uniquement sur les applications signées avec l’ancien certificat ne sera pas lu sur la nouvelle application (signée avec le nouveau certificat).

Si vous disposez d’une bibliothèque de contenu mise en liste blanche pour les applications signées avec un certificat de signature particulier et que ce certificat expire et que vous recevez un nouveau certificat (avec une paire de clés publique/privée différente), votre ancien contenu ne sera pas lu sur votre nouvelle application *sauf* si vous effectuez l’une des opérations suivantes :

* Utilisez une `PolicyUpdateList` page sur votre serveur de licences pour remplacer la stratégie entrante et insérez une nouvelle entrée de liste blanche d’application avec le résumé du nouveau certificat de signature.
* Mettez à jour la logique de votre serveur de licences afin de remplacer la stratégie entrante et d’insérer une nouvelle entrée de liste blanche d’applications.
* Demandez à l’émetteur du certificat de signature de vous délivrer un nouveau certificat qui utilise la même paire de clés publique/privée que celle utilisée par votre précédent certificat.
* Si vous fournissez du contenu HDS/HLS référençant un point de fin d’URL pour récupérer le fichier `DRMMetadata`, vous pouvez regénérer le fichier `DRMMetadata` (à l’aide du SDK Java DRM Primetime) pour insérer une nouvelle stratégie DRM contenant une entrée de liste blanche d’application mise à jour.

* Remplacez tout votre ancien contenu par une nouvelle stratégie DRM contenant le résumé de votre nouveau certificat de signature.

Voir `policy.allowedAIRApplication.n` Propriétés *de* configuration pour plus d’informations.

>[!NOTE]
>
>L’autorisation d’une application iOS requiert une approche spéciale. Reportez-vous à la [liste blanche de votre application](../../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-whitelist-your-ios-application.md) iOS dans le Guide *du programmeur* TVSDK pour iOS.