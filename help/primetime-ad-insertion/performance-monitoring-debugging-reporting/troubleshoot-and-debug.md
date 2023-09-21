---
title: Dépannage et débogage
description: Dépannage et débogage
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# Dépannage et débogage {#troubleshooting-debugging}

Primetime Ad Insertion propose des outils pour identifier et diagnostiquer les problèmes qui peuvent se produire dans toutes les phases de la diffusion vidéo, tels que les erreurs de diffusion CDN, les erreurs de création ou les erreurs de connectivité du client.

L’Ad Insertion Primetime prend en charge la journalisation détaillée via [Paramètre de l’API Bootstrap](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) `ptdebug=true` ou `ptdebug=AdCall` à l’URL de l’amorçage. Les journaux sont générés à la fois pour les en-têtes de réponse HTTP et pour la console de l’Ad Insertion Primetime. Ce paramètre est destiné uniquement aux tests localisés, et non aux flux de production. Pour plus d’informations sur les types de message lorsque la journalisation en mode verbeux est activée, voir [événements de journalisation de ptdebug dans la journalisation de verbose](verbose-logging.md#ptdebug-logging-events).

L’Ad Insertion Primetime fournit également un débogage des performances pour toutes les requêtes avec l’en-tête X-ADBE-AI-X1, qui peut être utilisé pour mesurer les performances et ajouter des insertions pour une requête donnée. Cet en-tête de requête est disponible, que la journalisation en mode verbeux soit activée ou non. Pour plus d’informations, voir [En-têtes verbeux : X-ADBE-PTAI-X1](debugging-headers.md).
