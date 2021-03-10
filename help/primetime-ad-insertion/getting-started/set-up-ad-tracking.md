---
title: Configuration du suivi des publicités
description: Configuration du suivi des publicités
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# Configurer le suivi des publicités {#ser-up-ad-tracking}

La plupart des annonceurs ont besoin d’informations sur le moment, la durée et le succès de l’affichage de leurs publicités. L’Ad Insertion Primetime prend en charge le suivi des publicités côté client, côté serveur et hybride afin de vous permettre de collecter plus facilement ces informations.

## Suivi des publicités côté client avec VMAP/JSON {#client-side-ad-tracking-vmap-json}

Dans le suivi des publicités côté client, le serveur envoie au client une structure JSON, VMAP ou in-manifest spécifiant les événements de suivi et les URL, ainsi que la liste de lecture assemblée.

Pour activer le suivi des publicités côté client, spécifiez les paramètres suivants dans l&#39;[API du Bootstrap](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

* `pttrackingmode=simple`

* `pttrackingversion={format version (vmap,v1,v2,v3)}`

>[!NOTE]
>
>Si vous définissez `pttrackingmode=simple`, la demande initiale d’API d’amorçage renvoie une réponse JSON, plutôt qu’un document HLS ou DASH.

<!-- **Daniel to check. The specified file in this statement does not exist.** 
More information about `pttrackingmode`, `pttrackingversion` formats, can be found in [API Reference: Manifest server query parameters](manifest-server-query-parameters.md). -->

<!--Show examples of how to request a sidecar] -->

## Suivi des publicités côté serveur {#server-side-ad-tracking}

Grâce à cette méthode, les données de suivi des publicités sont entièrement calculées côté serveur. Cela s’avère utile lorsque la mise à jour de l’application cliente n’est pas possible. Cependant, le suivi des publicités côté serveur peut ne pas correspondre à l’activité de lecture côté client. Par exemple, le serveur considère qu’une publicité est lue après la diffusion des segments, même si l’utilisateur final ne vue pas la totalité de la publicité.

Pour activer le suivi des publicités côté serveur, spécifiez le paramètre suivant dans l’[API du Bootstrap](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

`pttrackingmode=sstm`

Voir les sections `pttrackingmode` de l&#39;[API du Bootstrap](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

Toutes les balises de suivi des publicités sont envoyées avec les en-têtes de requête HTTP suivants :

* `X-Forwarded-For`
* `User-Agent`
* `X-Device-User-Agent`

Ces valeurs contiennent l’agent utilisateur/lecteur et l’adresse IP du client.

## Suivi des publicités hybrides {#hybrid-ad-tracking}

Cette approche est similaire au suivi côté serveur, mais l’application cliente demande également des sidecars à l’Ad Insertion Primetime pour obtenir des informations de suivi détaillées. Le suivi des publicités hybrides peut fournir des publicités non linéaires, telles que des incrustations et des compagnons, à l’application cliente, tout en continuant à compter sur l’Ad Insertion Primetime pour envoyer des URL de suivi des publicités individuelles.
Pour activer le suivi des publicités hybrides, reportez-vous au paramètre `pttrackingmode` de l&#39;[API du Bootstrap](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).