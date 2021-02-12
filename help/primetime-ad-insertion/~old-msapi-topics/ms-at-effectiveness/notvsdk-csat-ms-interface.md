---
description: Utilisez les paramètres facultatifs de requête pttrackingmode, pttrackingversion et pttrackingposition pour obtenir les URL vers lesquelles envoyer les informations de suivi des publicités sur la vidéo en cours. Les réponses varient selon la version de suivi et si le flux vidéo est en direct ou à la demande (VOD).
seo-description: Utilisez les paramètres facultatifs de requête pttrackingmode, pttrackingversion et pttrackingposition pour obtenir les URL vers lesquelles envoyer les informations de suivi des publicités sur la vidéo en cours. Les réponses varient selon la version de suivi et si le flux vidéo est en direct ou à la demande (VOD).
seo-title: API permettant aux lecteurs d’interagir avec le serveur de manifeste
title: API permettant aux lecteurs d’interagir avec le serveur de manifeste
uuid: ab7a19e7-6c28-4960-a56b-3b33c525e6b3
translation-type: tm+mt
source-git-commit: e1e33d3ac0aad44859cd49566331524da72ac7e4
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---


# API permettant aux lecteurs d&#39;interagir avec le serveur de manifeste {#api-for-players-to-interact-with-the-manifest-server}

Utilisez les paramètres de requête facultatifs `pttrackingmode`, `pttrackingversion` et `pttrackingposition` pour obtenir les URL vers lesquelles envoyer les informations de suivi des publicités sur la vidéo en cours. Les réponses varient selon la version de suivi et si le flux vidéo est en direct ou à la demande (VOD).

## Paramètres de requête {#query-parameters}

**pttrackingmode**

Exemple : `pttrackingmode=simple`
Le fait de spécifier simple indique au serveur de manifeste que vous souhaitez obtenir des informations de suivi.
Spécifiez-le sur une requête pour récupérer le M3U8 avant de demander des informations de suivi. Lorsque vous ne les spécifiez pas, le serveur de manifeste renvoie des informations de suivi dans les balises #EXT-X-MARKER.
Ou, si vous spécifiez une valeur valide autre que simple, le suivi côté serveur est appelé.

**pttrackingversion**

Exemple : `pttrackingversion=v2`
Ce paramètre indique au serveur de manifeste le format à utiliser pour renvoyer les informations de suivi (voir [Formats de fichier](/help/primetime-ad-insertion/~old-msapi-topics/ms-list-file-formats/ms-api-file-formats.md)).
Spécifiez-le sur une requête pour récupérer le M3U8 avant de demander des informations de suivi. Lorsque vous ne le spécifiez pas ou spécifiez une valeur non valide, le serveur de manifeste utilise v1.

**pttrackingposition**

Exemple : `pttrackingposition`
Ce paramètre indique au serveur de manifeste de renvoyer les informations de suivi de la vidéo sous la forme d&#39;un objet JSON ou VMAP dans le fichier M3U8. Le serveur de manifeste ignore la valeur spécifiée et envoie toutes les informations de suivi dont il dispose pour cette session. Si aucune valeur n’est transmise, le serveur de manifeste renvoie le fichier M3U8 demandé.
