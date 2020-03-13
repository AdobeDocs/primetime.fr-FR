---
description: Pour ceux qui connaissent bien la solution DRM d’Adobe Primetime Access, il existe des différences architecturales fondamentales entre Access et le DRM de Primetime Cloud, optimisé par la solution ExpressPlay.
seo-description: Pour ceux qui connaissent bien la solution DRM d’Adobe Primetime Access, il existe des différences architecturales fondamentales entre Access et le DRM de Primetime Cloud, optimisé par la solution ExpressPlay.
seo-title: Migration de l’accès à plusieurs DRM
title: Migration de l’accès à plusieurs DRM
uuid: 3e33ca9a-867e-46b8-bf88-8dbfe14ff786
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Migration de l’accès à plusieurs DRM {#migrating-from-access-to-multi-drm}

Pour ceux qui connaissent bien la solution DRM d’Adobe Primetime Access, il existe des différences architecturales fondamentales entre Access et le DRM de Primetime Cloud, optimisé par la solution ExpressPlay.

## Différences architecturales entre l’accès et le DRM multiple

|  | Accès | Multi-DRM |
|---|---|---|
| **Emballage** | Packager est lié à un serveur de licences. Packager doit connaître la clé publique du serveur de licences lorsque le contenu est compressé. | Packager n’est lié à aucun serveur de licences. |
|  | Une fois le contenu compressé, il est lié à un serveur de licences particulier. | Le contenu n’est pas lié à un serveur de licences spécifique. Cela a pour effet de créer un package de tout votre contenu avant d’obtenir votre licence de production. |
|  | Il n’est pas nécessaire que Packager communique avec une forme quelconque de  de clés , car les clés sont solidement intégrées dans le contenu lui-même (dans les métadonnées) après avoir été chiffrées. Seul le serveur de licences correspondant peut les lire. | Les clés doivent être envoyées *aux* Packagers à partir d&#39;un système  de clé, ou envoyées ** d&#39;un Packager à un système de de  clé. Un système de  clé  peut être soit le propre système d&#39;un client, soit le de  clé d&#39;ExpressPlay. |
| **Droit** | Le client effectue une demande de contenu au service Access Cloud. Le service Cloud Access émet ensuite une requête au système de droits du client. Le système de droits du client répond avec les droits du client. (Le client a probablement reçu un cookie pour se connecter sur les serveurs du client avant d’effectuer la demande de licence.) | Le client émet une demande de jeton à partir de la vitrine du client (il s’agit probablement du même processus au cours duquel le client recevait auparavant un cookie d’authentification). Actuellement, le client effectue une vérification des droits. Si la vérification des droits est terminée, le client envoie une demande aux serveurs ExpressPlay pour générer un jeton pour le client. Ce jeton est toujours lié à un élément de contenu spécifique et *peut* être lié à un périphérique spécifique. La vitrine du client renvoie le jeton au client. Lorsque le client effectue une demande de lecture DRM, le jeton est inclus dans la demande (la méthode est spécifique au périphérique) et le serveur DRM d&#39;ExpressPlay valide le jeton sans appeler le serveur du client. |