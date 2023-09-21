---
description: Le serveur de manifeste coordonne les systèmes qui fournissent du contenu, des publicités, de la lecture vidéo et du suivi des publicités. Il reçoit des listes de lecture (manifestes) codées en M3U8 que les lecteurs vidéo clients reçoivent des fournisseurs de contenu, assemble les publicités des fournisseurs de publicités dans les manifestes et transmet les manifestes assemblés aux lecteurs vidéo. Il prend en charge le suivi des publicités côté client et côté serveur. Elle effectue ses interactions à l’aide d’une interface de service Web basée sur HTTP.
title: Présentation des interactions entre le serveur de manifeste
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---


# Présentation des interactions entre le serveur de manifeste {#overview-of-manifest-server-interactions}

Le serveur de manifeste coordonne les systèmes qui fournissent du contenu, des publicités, de la lecture vidéo et du suivi des publicités. Il reçoit des listes de lecture (manifestes) codées en M3U8 que les lecteurs vidéo clients reçoivent des fournisseurs de contenu, assemble les publicités des fournisseurs de publicités dans les manifestes et transmet les manifestes assemblés aux lecteurs vidéo. Il prend en charge le suivi des publicités côté client et côté serveur. Elle effectue ses interactions à l’aide d’une interface de service Web basée sur HTTP.

Une configuration standard contient :

* Serveur de manifeste Primetime
* Le service de reconditionnement créatif Primetime (CRS)
* un client, contrôle d’un lecteur vidéo ;
* Un éditeur, généralement avec un système de gestion de contenu (CMS)
* Un réseau de diffusion de contenu (CDN)
* Un serveur de publicités
* Destinataire des rapports de suivi des publicités

Le workflow varie en fonction de plusieurs facteurs, comme si le réseau de diffusion de contenu est Akamai ou si le client effectue le suivi des publicités. Pour obtenir un diagramme du workflow pour le suivi des publicités côté client, voir [Workflow de suivi côté client](/help/primetime-ad-insertion/~old-msapi-topics/ms-at-effectiveness/notvsdk-csat-overview.md#section_cst_flow).

Le serveur de manifeste interagit avec les clients de diffusion vidéo en recevant et en répondant aux demandes de GET HTTP. Les réponses sont des manifestes codés en M3U8 décrivant le contenu assemblé par des annonces, incluant éventuellement une structure JSON ou VMAP (sidecar) contenant des instructions détaillées de suivi des publicités (voir [Formats de fichier](/help/primetime-ad-insertion/~old-msapi-topics/ms-list-file-formats/ms-api-file-formats.md)).

Un workflow type ressemble à ce qui suit :

1. L’éditeur envoie l’URL de contenu et les informations du serveur d’annonces au client.
1. Le client utilise les informations de l’éditeur pour générer une URL de serveur de manifeste et envoie une demande de GET à cette URL. Il s’agit de l’URL du Bootstrap.
1. Le serveur de manifeste établit une session avec le client.
1. Le serveur de manifeste obtient des manifestes de contenu à partir du réseau de diffusion de contenu, qui peuvent inclure des informations de coupure publicitaire.
1. Le serveur de manifeste redirige le client vers le manifeste maître/variante qu’il a généré pour le client.

   >[!NOTE]
   >
   >Si les paramètres de requête de l’URL du Bootstrap contiennent la variable `pttrackingmode=simple` ou `ptplayer=ios-mobileweb` , le serveur manifest renvoie l’URL du manifeste maître/variante dans un objet JSON, et le client envoie une demande de GET à cette URL de manifeste de variante.

1. Le client choisit un flux dans le manifeste de variante généré à lire, en envoyant des informations d’annonce au serveur de manifeste.
1. Le serveur de manifeste transmet les informations fournies par le client au serveur de publicités et reçoit les publicités et les URL de suivi des publicités du serveur de publicités. Si une publicité fournie n’est pas au format HLS, le serveur de manifeste l’envoie à CRS pour la conversion au format HLS.
1. Le serveur de manifeste regroupe des publicités dans le manifeste de contenu et envoie le nouveau manifeste assemblé au client.
1. Le client lit le contenu avec les publicités regroupées et envoie des requêtes aux URL de suivi spécifiées aux moments spécifiés.

L’insertion de publicités Primetime prend en charge les clients sur de nombreuses plateformes de diffusion vidéo. Tous les clients ne sont pas créés sur le package Primetime TVSDK, mais tous les clients envoient des demandes de GET vers la même URL de base. Les paramètres de requête permettent de distinguer une requête client d’une autre en indiquant au serveur manifeste :

* le client qui effectue la demande,
* ce que ce client veut,
* et les informations de suivi des publicités à fournir.

## CORS {#section_BEA7F298660944BE92801E4C82FCD038}

Le serveur de manifeste utilise la norme CORS (Cross-Origin Resource Sharing). Il recherche une `Origin` dans les requêtes qu’il reçoit. Si l’en-tête est présent, il répond avec

* `Access-Control-Allow-Origin: *`Chaîne de l’en-tête Origin`*`
* `Access-Control-Allow-Credentials: true`
* `Access-Control-Allow-Methods: GET`

Dans le cas contraire, il répond avec :

* `Access-Control-Allow-Origin: *`
* `Access-Control-Allow-Methods: GET`