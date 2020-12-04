---
description: Pour ceux qui connaissent la solution DRM d'accès à Adobe Primetime, il existe des différences architecturales fondamentales entre Access et le DRM de Cloud Primetime, optimisé par la solution ExpressPlay.
seo-description: Pour ceux qui connaissent la solution DRM d'accès à Adobe Primetime, il existe des différences architecturales fondamentales entre Access et le DRM de Cloud Primetime, optimisé par la solution ExpressPlay.
seo-title: Migration d’un accès à plusieurs DRM
title: Migration d’un accès à plusieurs DRM
uuid: 3e33ca9a-867e-46b8-bf88-8dbfe14ff786
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---


# Migration de l’accès à un DRM multiple {#migrating-from-access-to-multi-drm}

Pour ceux qui connaissent la solution DRM d&#39;accès à Adobe Primetime, il existe des différences architecturales fondamentales entre Access et le DRM de Cloud Primetime, optimisé par la solution ExpressPlay.

## Différences architecturales entre l&#39;accès et la gestion multi-DRM

|  | Accès | Multi-DRM |
|---|---|---|
| **Packaging** | Packager est lié à un serveur de licences. Packager doit connaître la clé publique du serveur de licences lorsque le contenu est compressé. | Packager n’est pas lié à un seul serveur de licences. |
|  | Une fois le contenu compressé, il est lié à un serveur de licences particulier. | Le contenu n’est pas lié à un serveur de licences spécifique. Cela a pour effet que vous pouvez assembler tout votre contenu avant d’obtenir votre licence de production. |
|  | Packager n’a pas besoin de communiquer avec un enregistrement de clé, car les clés sont solidement intégrées au contenu lui-même (dans les métadonnées) après avoir été chiffrées. Seul le serveur de licences correspondant peut les lire. | Les clés doivent être envoyées *à* Packagers à partir d&#39;un système d&#39;enregistrement clé ou envoyées *à partir de* Packager vers un système d&#39;enregistrement clé. Un système d&#39;enregistrement clé peut être soit le propre système d&#39;un client, soit l&#39;Enregistrement clé d&#39;ExpressPlay. |
| **Droit** | Le client envoie une demande de contenu au service Access Cloud. Le service Cloud d’accès envoie ensuite une demande au système de droits du client. Le système de droits du client répond aux droits du client. (Le client a probablement reçu un cookie de connexion des serveurs du client avant d’effectuer la demande de licence.) | Le client demande un jeton à partir de la vitrine du client (il s’agit probablement du même processus au cours duquel le client recevait auparavant un cookie d’authentification). Actuellement, le client effectue une vérification des droits. Si la vérification des droits est effectuée, le client envoie une demande aux serveurs ExpressPlay pour générer un jeton pour le client. Ce jeton est toujours lié à un élément de contenu spécifique et *peut* être lié à un périphérique spécifique. La vitrine du client renvoie le jeton au client. Lorsque le client effectue une demande de lecture DRM, le jeton est inclus dans la demande (la méthode est spécifique au périphérique) et le serveur DRM d&#39;ExpressPlay valide le jeton sans appeler le serveur du client. |