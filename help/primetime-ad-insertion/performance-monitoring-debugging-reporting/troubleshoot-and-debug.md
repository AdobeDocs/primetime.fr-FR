---
title: Résolution des problèmes et débogage
description: null
translation-type: tm+mt
source-git-commit: 242b5a2875ebc0e0020296ce9489dd54438b5ad0
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---


# Dépannage et débogage {#troubleshooting-debugging}

Outils d’offres Ad Insertion Primetime permettant d’identifier et de diagnostiquer les problèmes qui peuvent se produire à toutes les phases de la diffusion vidéo, tels que les erreurs de diffusion CDN, les erreurs créatives ou les erreurs de connectivité client.

L’Ad Insertion Primetime prend en charge la journalisation détaillée par le biais du paramètre [API du Bootstrap](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) `ptdebug=true` ou `ptdebug=AdCall` de l’URL d’amorçage. Les journaux sont générés à la fois dans les en-têtes de réponse HTTP et dans la console de l’Ad Insertion Primetime. Ce paramètre est destiné aux tests localisés uniquement, et non aux flux de production. Pour plus d&#39;informations sur les types de messages lorsque la journalisation des verboses est activée, consultez [événements de journalisation de ptdebug dans la journalisation des verboses](verbose-logging.md#ptdebug-logging-events).

L’Ad Insertion Primetime fournit également un débogage des performances sur toutes les requêtes avec l’en-tête X-ADBE-AI-X1, qui peut être utilisé pour mesurer les performances et les insertions publicitaires sur une requête donnée. Cet en-tête de requête est disponible, que la journalisation détaillée soit activée ou non. Pour plus d’informations, voir en-têtes [Verbose : X-ADBE-PTAI-X1](debugging-headers.md).
