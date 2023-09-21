---
description: Utilisez les paramètres de requête optionnels pttrackingmode, pttrackingversion et pttrackingposition pour obtenir des URL vers lesquelles envoyer des informations de suivi des publicités sur la vidéo en cours. Les réponses varient selon la version de suivi et si la diffusion vidéo est en direct ou sur demande (VOD).
title: API permettant aux lecteurs d’interagir avec le serveur manifeste
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# API permettant aux lecteurs d’interagir avec le serveur manifeste {#api-for-players-to-interact-with-the-manifest-server}

Utilisez le paramètre facultatif `pttrackingmode`, `pttrackingversion`, et `pttrackingposition` paramètres de requête pour obtenir des URL auxquelles envoyer des informations de suivi publicitaire sur la vidéo actuelle. Les réponses varient selon la version de suivi et si la diffusion vidéo est en direct ou sur demande (VOD).

## Paramètres de requête {#query-parameters}

**pttrackingmode**

Exemple : `pttrackingmode=simple`
Le fait de spécifier simple indique au serveur de manifeste que vous souhaitez obtenir des informations de suivi.
Spécifiez-le sur une requête pour récupérer le M3U8 avant de demander les informations de suivi. Lorsque vous ne les spécifiez pas, le serveur de manifeste renvoie les informations de suivi dans les balises #EXT-X-MARKER.
Ou, si vous spécifiez une valeur valide autre que simple, le suivi côté serveur est appelé.

**pttrackingversion**

Exemple : `pttrackingversion=v2`
Ce paramètre indique au serveur de manifeste le format à utiliser pour renvoyer les informations de suivi (voir [Formats de fichier](/help/primetime-ad-insertion/~old-msapi-topics/ms-list-file-formats/ms-api-file-formats.md)).
Spécifiez-le sur une requête pour récupérer le M3U8 avant de demander des informations de suivi. Lorsque vous ne le spécifiez pas ou spécifiez une valeur non valide, le serveur de manifeste utilise v1.

**pttrackingposition**

Exemple : `pttrackingposition`
Ce paramètre indique au serveur de manifeste de renvoyer les informations de suivi de la vidéo sous la forme d’un objet JSON ou VMAP dans le fichier M3U8. Le serveur de manifeste ignore la valeur spécifiée et envoie toutes les informations de suivi dont il dispose pour cette session. Si aucune valeur n’est transmise, le serveur manifest renvoie le fichier M3U8 demandé.
