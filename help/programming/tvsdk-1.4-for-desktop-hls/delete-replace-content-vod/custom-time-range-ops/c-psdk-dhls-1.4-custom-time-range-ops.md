---
description: TVSDK prend en charge la suppression et le remplacement programmatiques de contenu publicitaire dans les flux VOD.
title: Opérations de période personnalisées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Présentation {#custom-time-range-operations-overview}

TVSDK prend en charge la suppression et le remplacement programmatiques de contenu publicitaire dans les flux VOD.

La fonction de suppression et de remplacement étend la fonction de marqueurs d’annonce personnalisés. Les marqueurs de publicité personnalisés marquent les sections du contenu principal comme des périodes de contenu liées à la publicité. Outre le marquage de ces plages temporelles, vous pouvez également supprimer et remplacer des plages temporelles.

<!--<a id="section_D3FE668CAF764DCC912373D5410C932C"></a>-->

La suppression et le remplacement des publicités sont implémentés avec des marqueurs personnalisés qui identifient différents types de plages dans un flux VOD : marquer, supprimer et remplacer. Pour chaque période personnalisée, vous pouvez effectuer les opérations associées, y compris la suppression ou le remplacement de contenu publicitaire.

Pour la suppression et le remplacement des publicités, TVSDK comprend les éléments suivants : *opération de période personnalisée* modes :

* MARK - Dispatches `AdBreak` pour les régions marquées. (Cela s’appelait `customAdMarker` dans les versions précédentes de TVSDK.) L&#39;insertion d&#39;une publicité n&#39;est pas autorisée dans ce mode.

* DELETE : pour ce mode, l’application utilise la variable `TimeRangeCollection` pour définir des régions temporelles pour la suppression de publicités C3. L&#39;insertion d&#39;une publicité est autorisée dans ce mode.
* REPLACE : dans ce mode, l’application remplace un `timeRange` avec une prise de décision publicitaire Adobe Primetime `AdBreak`. L’opération de remplacement commence à l’endroit où la suppression de publicité C3 se produit et se termine à l’heure indiquée (plus courte ou plus longue que la période d’origine).

TVSDK fournit une `CustomRangesOpportunityGenerator` pour générer des opportunités d’emplacement pour les plages MARK et de DELETE. Pour le mode REPLACE, TVSDK génère deux opportunités de placement pour chaque période :

* La variable `CustomRangeResolver` génère des opportunités d’emplacement pour le DELETE
* La variable `AuditudeAdResolver` génère des opportunités de placement pour INSERT.
