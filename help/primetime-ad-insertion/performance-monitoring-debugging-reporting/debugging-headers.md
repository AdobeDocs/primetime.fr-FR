---
title: Débogage des en-têtes
description: Débogage des en-têtes
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 7%

---

# En-têtes de débogage (X-ADBE-AI-X1) {#debugging-headers}

SSAI envoie des en-têtes HTTP qui peuvent être utilisés pour collecter des informations et déterminer les performances des sessions de production, situées dans l’en-tête X-ADBE-AI-X1.

Exemple d’en-tête :
`X-ADBE-AI-X1: 0 1 1594181097704 15126333-5ba9-49b8-a219-4f37e60d259c v 0 1 30 2 1 199 2 185 497 204 104 0 1 0 4`

La description des champs est la suivante :

| Nom | Description | Exemple |
|--- |--- |--- |
| isActivePreroll | Envoi ou non d’un appel publicitaire pour le preroll | 0 |
| isActiveMidroll | Envoi ou non d’un appel publicitaire pour le mid-roll | 1 |
| ID de demande | SSAI interne | 1594181097704 |
| ID de session | ID de session de la requête | 15126333-5ba9-49b8-a219-4f37e60d259c |
| Type de diffusion | u=variant, l=live, v=vod | v |
| isBootstrap | Indique si cette requête est un appel de démarrage. | 0 |
| Nombre de coupures publicitaires | Nombre total de coupures publicitaires dans ce manifeste | 1 |
| Durée totale de coupure publicitaire | Durée totale de coupure publicitaire, en secondes | 30 |
| Nombre d’appels publicitaires | Nombre d’appels publicitaires envoyés dans cette requête | 2 |
| Nombre d’appels de redirection | Nombre d’appels de publicité de redirection envoyés dans cette requête | 1 |
| Durée totale de l’appel de publicité | Durée totale de traitement de l’appel publicitaire | 199 |
| Nombre de publicités insérées | Nombre de publicités insérées dans le manifeste | 2 |
| Heure de demande du manifeste source | Durée de récupération du contenu uniquement | 185 |
| Durée totale de la requête | Durée totale de la recherche de contenu et de publicités | 497 |
| Temps de récupération du manifeste publicitaire (total) | Durée totale de récupération des manifestes publicitaires | 204 |
| Temps de récupération du manifeste publicitaire (réel) | Durée réelle de récupération des manifestes publicitaires en parallèle | 104 |
| Accès au cache de contenu | Nombre d’accès au cache de contenu | 0 |
| Échec du cache de contenu | Nombre d’échecs du cache de contenu | 1 |
| Accès au cache du manifeste publicitaire | Nombre d’accès au cache du manifeste publicitaire | 0 |
| Échec du cache du manifeste de publicité | Nombre d’erreurs au cache du manifeste publicitaire | 4 |
