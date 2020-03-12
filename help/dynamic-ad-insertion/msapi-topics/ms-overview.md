---
description: Le serveur de manifeste coordonne les systèmes qui fournissent du contenu, fournissent des publicités, lisent des vidéos et suivent des publicités. Il reçoit des listes de lecture (manifestes) codées au format M3U8 que les lecteurs vidéo clients reçoivent des fournisseurs de contenu, stimule les publicités des fournisseurs de publicité dans les manifestes et transmet les manifestes assemblés aux lecteurs vidéo. Il prend en charge le suivi des publicités côté client et côté serveur. Il effectue ses interactions à l’aide d’une interface de service Web basée sur HTTP.
seo-description: Le serveur de manifeste coordonne les systèmes qui fournissent du contenu, fournissent des publicités, lisent des vidéos et suivent des publicités. Il reçoit des listes de lecture (manifestes) codées au format M3U8 que les lecteurs vidéo clients reçoivent des fournisseurs de contenu, stimule les publicités des fournisseurs de publicité dans les manifestes et transmet les manifestes assemblés aux lecteurs vidéo. Il prend en charge le suivi des publicités côté client et côté serveur. Il effectue ses interactions à l’aide d’une interface de service Web basée sur HTTP.
seo-title: Présentation des interactions du serveur de manifeste
title: Présentation des interactions du serveur de manifeste
uuid: 3e314a45-a4dd-492f-8915-19224a8fbbc7
translation-type: tm+mt
source-git-commit: 9dc8498593a1d70918b66016e429eb013cdc61f7

---


# Présentation des interactions du serveur de manifeste {#overview-of-manifest-server-interactions}

Le serveur de manifeste coordonne les systèmes qui fournissent du contenu, fournissent des publicités, lisent des vidéos et suivent des publicités. Il reçoit des listes de lecture (manifestes) codées au format M3U8 que les lecteurs vidéo clients reçoivent des fournisseurs de contenu, stimule les publicités des fournisseurs de publicité dans les manifestes et transmet les manifestes assemblés aux lecteurs vidéo. Il prend en charge le suivi des publicités côté client et côté serveur. Il effectue ses interactions à l’aide d’une interface de service Web basée sur HTTP.

Une configuration type contient :

* Serveur de manifeste Primetime
* Le service de reconditionnement créatif (CRS) Primetime
* Client, contrôle d’un lecteur vidéo
* Un éditeur, généralement avec un système de  (CMS)
* Un réseau CDN (Content Network)
* Un serveur de publicité
* Récepteur pour les rapports de suivi des publicités

Le flux de travaux varie selon un certain nombre de facteurs, comme si le CDN est Akamai ou si le client effectue le suivi des publicités. Pour obtenir un diagramme du flux de travail pour le suivi des publicités côté client, voir Flux de travail [de suivi côté](../msapi-topics/ms-at-effectiveness/notvsdk-csat-overview.md#section_cst_flow)client.

Le serveur de manifeste interagit avec les clients de  vidéo en recevant et en répondant aux demandes HTTP GET. Les réponses sont des manifestes codés au format M3U8 décrivant le contenu assemblé par publicité, incluant éventuellement une structure JSON ou VMAP (sidecar) contenant des instructions de suivi publicitaire détaillées (voir Formats [de](../msapi-topics/ms-list-file-formats/ms-api-file-formats.md)fichier).

Un flux de travail type se présente comme suit :

1. L’éditeur envoie au client l’URL de contenu et les informations relatives au serveur d’annonces.
1. Le client utilise les informations de l’éditeur pour générer une URL de serveur de manifeste et envoie une requête GET à cette URL. Il s’agit de l’URL d’amorçage.
1. Le serveur de manifeste établit une session avec le client.
1. Le serveur de manifeste récupère les manifestes de contenu du CDN, ce qui peut inclure des informations sur les coupures publicitaires.
1. Le serveur de manifeste redirige le client vers le manifeste maître/variante qu’il a généré pour le client.

   >[!NOTE]
   >
   >Si les paramètres du d’URL d’amorçage contiennent le paramètre `pttrackingmode=simple` ou `ptplayer=ios-mobileweb` , le serveur manifeste renvoie l’URL manifeste maître/variante dans un objet JSON et le client envoie une requête GET à cette URL de manifeste variante.

1. Le client sélectionne un flux dans le manifeste de variante généré à lire, en envoyant des informations publicitaires au serveur de manifeste.
1. Le serveur de manifeste transmet les informations fournies par le client au serveur d’annonces et reçoit les annonces et les URL de suivi des annonces du serveur d’annonces. Si une publicité fournie n’est pas au format HLS, le serveur de manifeste l’envoie à CRS pour la conversion au format HLS.
1. Le serveur de manifeste assemble les publicités dans le manifeste de contenu et envoie le nouveau manifeste assemblé au client.
1. Le client lit le contenu avec les publicités assemblées et envoie des requêtes aux URL de suivi spécifiées aux moments spécifiés.

L’insertion de publicités Primetime prend en charge les clients sur de nombreuses plateformes de  vidéo. Tous les clients ne sont pas construits sur le paquet Primetime TVSDK, mais tous les clients envoient des demandes GET vers la même URL de base. Les paramètres  du distinguent une requête client de l’autre en indiquant au serveur manifeste :

* le client qui fait la demande,
* ce que ce client veut,
* et les informations de suivi des publicités à fournir.

## CORS {#section_BEA7F298660944BE92801E4C82FCD038}

Le serveur de manifeste utilise la norme CORS (Cross-  Resource Sharing standard). Il recherche un `Origin` en-tête dans les requêtes qu’il reçoit. Si l’en-tête est présent, il répond par

* `Access-Control-Allow-Origin: *`chaîne de l’en-tête  du`*`
* `Access-Control-Allow-Credentials: true`
* `Access-Control-Allow-Methods: GET`

Dans le cas contraire, il répond par :

* `Access-Control-Allow-Origin: *`
* `Access-Control-Allow-Methods: GET`