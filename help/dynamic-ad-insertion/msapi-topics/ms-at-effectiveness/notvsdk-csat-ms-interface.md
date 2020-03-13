---
description: Utilisez les paramètres facultatifs du mode de suivi des modifications, de la version de suivi des modifications et de la position de suivi des modifications  pour obtenir des URL vers lesquelles envoyer des informations de suivi des publicités sur la vidéo en cours. Les réponses varient selon la version de suivi et si le flux vidéo est en direct ou à la demande (VOD).
seo-description: Utilisez les paramètres facultatifs du mode de suivi des modifications, de la version de suivi des modifications et de la position de suivi des modifications  pour obtenir des URL vers lesquelles envoyer des informations de suivi des publicités sur la vidéo en cours. Les réponses varient selon la version de suivi et si le flux vidéo est en direct ou à la demande (VOD).
seo-title: API permettant aux lecteurs d’interagir avec le serveur de manifeste
title: API permettant aux lecteurs d’interagir avec le serveur de manifeste
uuid: ab7a19e7-6c28-4960-a56b-3b33c525e6b3
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d

---


# API permettant aux lecteurs d’interagir avec le serveur de manifeste {#api-for-players-to-interact-with-the-manifest-server}

Utilisez les paramètres facultatifs `pttrackingmode`, `pttrackingversion`et `pttrackingposition` pour obtenir des URL vers lesquelles envoyer des informations de suivi des publicités sur la vidéo en cours. Les réponses varient selon la version de suivi et si le flux vidéo est en direct ou à la demande (VOD).

## Paramètres {#query-parameters}

|**pttrackingmode**|Exemple : pttrackingmode=simpleSpécifier simple indique au serveur de manifeste que vous souhaitez des informations de suivi.
Spécifiez-le lors d’une requête pour récupérer le M3U8 avant de demander des informations de suivi.Lorsque vous ne le spécifiez pas, le serveur de manifeste renvoie des informations de suivi dans les balises #EXT-X-MARKER.
Ou, si vous spécifiez une valeur valide autre que simple, le suivi côté serveur est appelé.

|**pttrackingversion**|Exemple : pttrackingversion=v2Ce paramètre indique au serveur de manifeste le format à utiliser pour renvoyer les informations de suivi (voir Formats [de](../../msapi-topics/ms-list-file-formats/ms-api-file-formats.md)fichier).
Spécifiez-le lors d&#39;une requête pour récupérer le M3U8 avant de demander des informations de suivi.Lorsque vous ne le spécifiez pas ou spécifiez une valeur non valide, le serveur de manifeste utilise v1.

|**pttrackingposition**|Exemple : pttrackingpositionCe paramètre indique au serveur de manifeste de renvoyer les informations de suivi de la vidéo sous la forme d&#39;un objet JSON ou VMAP dans le fichier M3U8. Le serveur de manifeste ignore la valeur spécifiée et envoie toutes les informations de suivi dont il dispose pour cette session. Si aucune valeur n’est transmise, le serveur de manifeste renvoie le fichier M3U8 demandé.