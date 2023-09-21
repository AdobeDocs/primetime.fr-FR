---
description: Pour ceux qui maîtrisent la solution DRM Primetime Access d’Adobe, il existe des différences architecturales fondamentales entre Access et Primetime Cloud DRM, optimisé par la solution ExpressPlay.
title: Migration de l’accès à plusieurs DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Migration de l’accès à plusieurs DRM {#migrating-from-access-to-multi-drm}

Pour ceux qui maîtrisent la solution DRM Primetime Access d’Adobe, il existe des différences architecturales fondamentales entre Access et Primetime Cloud DRM, optimisé par la solution ExpressPlay.

## Différences architecturales entre l’accès et le multi-DRM

|  | Accès | Multi-DRM |
|---|---|---|
| **Modules** | Le Packager est lié à un serveur de licences. Le Packager doit connaître la clé publique du serveur de licences lorsque le contenu est compressé. | Le Packager n’est pas lié à un seul serveur de licences. |
|  | Une fois le contenu empaqueté, il est lié à un serveur de licences spécifique. | Le contenu n’est pas lié à un serveur de licences spécifique. Vous pouvez ainsi regrouper tout votre contenu avant d’obtenir votre licence de production. |
|  | Il n’est pas nécessaire que le Packager communique avec une forme ou une autre de stockage de clés, car les clés sont incorporées en toute sécurité dans le contenu lui-même (dans les métadonnées) après avoir été chiffrées. Seul le serveur de licences correspondant peut les lire. | Les clés doivent être envoyées *to* Packagers à partir d’un système de stockage clé ou envoyés *de* un Packager vers un système de stockage clé. Un système de stockage clé peut être soit le propre système d’un client, soit le Key Storage d’ExpressPlay. |
| **Droit** | Le client effectue une demande de contenu auprès du service Access Cloud. Le service cloud d’accès envoie ensuite une demande au système de droits du client. Le système de droits du client répond avec les droits pour le client. (Le client a probablement reçu un cookie pour se connecter à partir des serveurs du client avant d’effectuer la demande de licence.) | Le client effectue une demande de jeton depuis le storefront du client (il s’agit probablement du même workflow dans lequel le client obtenait auparavant un cookie d’authentification). Actuellement, le client effectue une vérification des droits. Si la vérification des droits est effectuée, le client envoie une demande aux serveurs ExpressPlay afin de générer un jeton pour le client. Ce jeton est toujours lié à un élément de contenu spécifique, et *may* être lié à un appareil spécifique. Le storefront du client renvoie le jeton au client. Lorsque le client effectue une demande de lecture DRM, le jeton est inclus dans la demande (la méthode est spécifique à l’appareil), et le serveur DRM d’ExpressPlay valide le jeton sans appeler le serveur du client. |
