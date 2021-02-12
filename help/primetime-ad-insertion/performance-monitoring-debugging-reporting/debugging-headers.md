---
title: Débogage des en-têtes
description: null
translation-type: tm+mt
source-git-commit: 45e5c8e6144adf4a405bde7d8d19505b7ad549e0
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 7%

---


# Débogage des en-têtes (X-ADBE-AI-X1) {#debugging-headers}

SSAI envoie des en-têtes HTTP qui peuvent être utilisés pour collecter des informations et déterminer les performances des sessions de production, situées dans l’en-tête X-ADBE-AI-X1.

Exemple d’en-tête :
`X-ADBE-AI-X1: 0 1 1594181097704 15126333-5ba9-49b8-a219-4f37e60d259c v 0 1 30 2 1 199 2 185 497 204 104 0 1 0 4`

La description des champs est la suivante :

| Nom | Description | Exemple |
|--- |--- |--- |
| isActivePreroll | Envoi ou non d’un appel publicitaire pour la pré-diffusion | 0 |
| isActiveMidroll | Envoi ou non d’un appel publicitaire pour le déroulement intermédiaire | 1 |
| ID de demande | SSAI interne | 1594181097704 |
| ID de session | ID de session de la requête | 1512633-5ba9-49b8-a219-4f37e60d259c |
| Type de diffusion | u=variant, l=live, v=vod | v |
| isBootstrap | Indique si cette demande est un appel de démarrage | 0 |
| Nombre de coupures publicitaires | Nombre total de coupures publicitaires dans ce manifeste | 3 |
| Durée totale des pauses publicitaires | Durée totale de la coupure publicitaire, en secondes | 30 |
| Nombre d&#39;appels d&#39;annonce | Nombre d&#39;appels de publicité envoyés dans cette demande | 2 |
| Nombre d&#39;appels de redirection | Nombre d&#39;appels de publicité de redirection envoyés dans cette demande | 1 |
| Durée totale des appels publicitaires | Durée totale de traitement des appels d’annonce | 1999 |
| Nombre d&#39;annonces insérées | Nombre de publicités insérées dans le manifeste | 2 |
| Heure de demande du manifeste source | Durée de récupération du contenu uniquement | 185 |
| Durée totale de la demande | Durée totale de la recherche de contenu et de publicités | 497 |
| Temps de récupération du manifeste publicitaire (total) | Durée totale de récupération des manifestes publicitaires | 204 |
| Heure de récupération du manifeste publicitaire (réelle) | Durée réelle de récupération et manifestes publicitaires en parallèle | 104 |
| Accès au cache de contenu | Nombre d’accès au cache de contenu | 0 |
| Échec du cache de contenu | Nombre d’échecs du cache de contenu | 3 |
| Accès au cache du manifeste publicitaire | Nombre d’accès au cache du manifeste publicitaire | 0 |
| Manque de cache du manifeste publicitaire | Nombre d&#39;échecs du cache du manifeste publicitaire | 4 |