---
title: Configuration du suivi des publicités
description: Configuration du suivi des publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Configuration du suivi des publicités {#ser-up-ad-tracking}

La plupart des annonceurs ont besoin d’informations sur le moment, la durée et le degré de succès de l’affichage de leurs publicités. Primetime Ad Insertion prend en charge le suivi des publicités hybride, côté client et côté serveur afin de garantir une certaine souplesse lors de la collecte de ces informations.

## Suivi des publicités côté client avec VMAP/JSON {#client-side-ad-tracking-vmap-json}

Dans le cadre du suivi des publicités côté client, le serveur envoie au client une structure JSON, VMAP ou in-manifest spécifiant les événements de suivi et les URL, ainsi que la liste de lecture groupée aux publicités.

Pour activer le suivi des publicités côté client, spécifiez les paramètres suivants dans la variable [API BOOTSTRAP](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

* `pttrackingmode=simple`

* `pttrackingversion={format version (vmap,v1,v2,v3)}`

>[!NOTE]
>
>La définition de la variable `pttrackingmode=simple` entraîne le renvoi d’une réponse JSON à la demande d’API de bootstrap initiale, plutôt qu’un document HLS ou DASH.

<!-- **Daniel to check. The specified file in this statement does not exist.** 
More information about `pttrackingmode`, `pttrackingversion` formats, can be found in [API Reference: Manifest server query parameters](manifest-server-query-parameters.md). -->

<!--Show examples of how to request a sidecar] -->

## Suivi des publicités côté serveur {#server-side-ad-tracking}

Grâce à cette méthode, les données de suivi des publicités sont entièrement calculées côté serveur. Cela s’avère utile lorsque la mise à jour de l’application cliente n’est pas possible. Cependant, le suivi des publicités côté serveur peut ne pas correspondre à l’activité de lecture côté client. Par exemple, le serveur considère qu’une publicité doit être lue une fois les segments distribués, même si l’utilisateur final ne voit pas l’intégralité de la publicité.

Pour activer le suivi des publicités côté serveur, spécifiez le paramètre suivant dans la variable [API BOOTSTRAP](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

`pttrackingmode=sstm`

Voir `pttrackingmode` sections de [API BOOTSTRAP](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

Toutes les balises de suivi des publicités sont envoyées avec les en-têtes de requête HTTP suivants :

* `X-Forwarded-For`
* `User-Agent`
* `X-Device-User-Agent`

Ces valeurs contiennent l’adresse IP du client/agent utilisateur du lecteur et l’adresse IP du client.

## Suivi des publicités hybrides {#hybrid-ad-tracking}

Cette approche est semblable au suivi côté serveur, mais l’application client demande également des sidecars de l’Ad Insertion Primetime pour obtenir des informations de suivi détaillées. Le suivi des publicités hybrides peut diffuser des publicités non linéaires telles que des superpositions et des compagnons vers l’application cliente, tout en comptant sur l’Ad Insertion Primetime pour envoyer des URL de suivi des publicités individuelles.
Pour activer le suivi des publicités hybrides, voir `pttrackingmode` du paramètre [API BOOTSTRAP](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).
