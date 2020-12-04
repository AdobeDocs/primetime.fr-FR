---
description: Le serveur de manifeste coordonne les systèmes qui fournissent du contenu, fournissent des publicités, lisent des vidéos et effectuent le suivi des publicités. Il reçoit des listes de lecture (manifestes) codées en M3U8 que les lecteurs vidéo clients reçoivent des fournisseurs de contenu, sélectionne les publicités des fournisseurs de publicité dans les manifestes et transmet les manifestes assemblés aux lecteurs vidéo. Il prend en charge le suivi des publicités côté client et côté serveur. Il effectue ses interactions à l’aide d’une interface de service Web basée sur HTTP.
seo-description: Le serveur de manifeste coordonne les systèmes qui fournissent du contenu, fournissent des publicités, lisent des vidéos et effectuent le suivi des publicités. Il reçoit des listes de lecture (manifestes) codées en M3U8 que les lecteurs vidéo clients reçoivent des fournisseurs de contenu, sélectionne les publicités des fournisseurs de publicité dans les manifestes et transmet les manifestes assemblés aux lecteurs vidéo. Il prend en charge le suivi des publicités côté client et côté serveur. Il effectue ses interactions à l’aide d’une interface de service Web basée sur HTTP.
seo-title: Présentation des interactions du serveur de manifeste
title: Présentation des interactions du serveur de manifeste
uuid: 3e314a45-a4dd-492f-8915-19224a8fbbc7
translation-type: tm+mt
source-git-commit: 9dc8498593a1d70918b66016e429eb013cdc61f7
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 0%

---


# Présentation des interactions du serveur de manifeste {#overview-of-manifest-server-interactions}

Le serveur de manifeste coordonne les systèmes qui fournissent du contenu, fournissent des publicités, lisent des vidéos et effectuent le suivi des publicités. Il reçoit des listes de lecture (manifestes) codées en M3U8 que les lecteurs vidéo clients reçoivent des fournisseurs de contenu, sélectionne les publicités des fournisseurs de publicité dans les manifestes et transmet les manifestes assemblés aux lecteurs vidéo. Il prend en charge le suivi des publicités côté client et côté serveur. Il effectue ses interactions à l’aide d’une interface de service Web basée sur HTTP.

Une configuration type contient :

* Serveur de manifeste Primetime
* Service de reconditionnement créatif (CRS) de Primetime
* Client, contrôle d’un lecteur vidéo
* Un éditeur, généralement avec un système de Gestion de contenu (CMS)
* Un réseau CDN (Content Diffusion Network)
* Un serveur d’annonces
* Récepteur pour les rapports de suivi des publicités

Le flux de travaux varie en fonction de plusieurs facteurs, comme si le réseau de diffusion de contenu est Akamai ou si le client effectue le suivi des publicités. Pour obtenir un diagramme du processus de suivi des publicités côté client, voir [Processus de suivi côté client](../msapi-topics/ms-at-effectiveness/notvsdk-csat-overview.md#section_cst_flow).

Le serveur de manifeste interagit avec les clients de diffusion vidéo en recevant et en répondant aux demandes de GET HTTP. Les réponses sont des manifestes codés en M3U8 décrivant le contenu assemblé par des annonces publicitaires, incluant éventuellement une structure JSON ou VMAP (sidecar) contenant des instructions détaillées de suivi publicitaire (voir [Formats de fichier](../msapi-topics/ms-list-file-formats/ms-api-file-formats.md)).

Un flux de travaux type ressemble à ce qui suit :

1. L’éditeur envoie l’URL de contenu et les informations relatives au serveur d’annonces au client.
1. Le client utilise les informations de l’éditeur pour générer une URL de serveur de manifeste et envoie une demande de GET à cette URL. Il s’agit de l’URL du Bootstrap.
1. Le serveur de manifeste établit une session avec le client.
1. Le serveur de manifeste récupère les manifestes de contenu du réseau de diffusion de contenu, ce qui peut inclure des informations sur les coupures publicitaires.
1. Le serveur de manifeste redirige le client vers le manifeste maître/variante qu’il a généré pour le client.

   >[!NOTE]
   >
   >Si les paramètres de requête d&#39;URL du Bootstrap contiennent le paramètre `pttrackingmode=simple` ou `ptplayer=ios-mobileweb`, le serveur de manifeste renvoie l&#39;URL de manifeste maître/variante dans un objet JSON et le client envoie une demande de GET à cette URL de manifeste de variante.

1. Le client sélectionne un flux dans le manifeste de variante généré à lire, en envoyant des informations publicitaires au serveur de manifeste.
1. Le serveur de manifeste transmet les informations fournies par le client au serveur d’annonces et reçoit les annonces et les URL de suivi des annonces du serveur d’annonces. Si une publicité fournie n&#39;est pas au format HLS, le serveur de manifeste l&#39;envoie à CRS pour la conversion au format HLS.
1. Le serveur de manifeste rassemble les publicités dans le manifeste de contenu et envoie le nouveau manifeste assemblé au client.
1. Le client lit le contenu avec les publicités assemblées et envoie des requêtes aux URL de suivi spécifiées aux moments spécifiés.

L’insertion d’annonces Primetime prend en charge les clients sur de nombreuses plateformes de diffusion vidéo. Tous les clients ne sont pas construits sur le package TVSDK Primetime, mais tous les clients envoient des demandes de GET à la même URL de base. Les paramètres de requête permettent de distinguer une requête client d’une autre en indiquant au serveur manifeste :

* le client qui fait la demande,
* ce que ce client veut,
* et les informations de suivi publicitaire à fournir.

## CORS {#section_BEA7F298660944BE92801E4C82FCD038}

Le serveur de manifeste utilise la norme CORS (Cross Origine Resource Sharing). Il recherche un en-tête `Origin` dans les requêtes qu’il reçoit. Si l’en-tête est présent, il répond par

* `Access-Control-Allow-Origin: *`chaîne de l’en-tête de l’Origine`*`
* `Access-Control-Allow-Credentials: true`
* `Access-Control-Allow-Methods: GET`

Dans le cas contraire, elle répond par :

* `Access-Control-Allow-Origin: *`
* `Access-Control-Allow-Methods: GET`