---
description: TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.
seo-description: TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.
seo-title: Opérations de plage de temps personnalisées
title: Opérations de plage de temps personnalisées
uuid: fb27f343-718d-444e-8fc1-5ae0be02557b
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Présentation {#custom-time-range-operations-overview}

TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.

La fonction de suppression et de remplacement étend la fonction des marqueurs publicitaires personnalisés. Les marqueurs publicitaires personnalisés marquent les sections du contenu principal comme des périodes de contenu liées aux publicités. Outre le marquage de ces plages de temps, vous pouvez également supprimer et remplacer des plages de temps.

<!--<a id="section_D3FE668CAF764DCC912373D5410C932C"></a>-->

La suppression et le remplacement des publicités sont implémentés avec des marqueurs personnalisés qui identifient différents types de périodes dans un flux VOD : marquer, supprimer et remplacer. Pour chaque période personnalisée, vous pouvez effectuer les opérations associées, y compris la suppression ou le remplacement du contenu d’une publicité.

Pour la suppression et le remplacement des publicités, TVSDK inclut les modes *personnalisés d’opération* de plage de temps suivants :

* MARK - Distribue `AdBreak` des  pour les régions marquées. (Ce nom a été appelé `customAdMarker` dans les versions précédentes de TVSDK.) L’insertion d’une publicité n’est pas autorisée dans ce mode.

* DELETE - Dans ce mode, l’application utilise la `TimeRangeCollection` classe pour définir des régions temporelles pour la suppression des publicités C3. L’insertion d’une publicité est autorisée dans ce mode.
* REMPLACER - Dans ce mode, l’application remplace un `timeRange` par une décision publicitaire Adobe Primetime `AdBreak`. L’opération de remplacement  l’endroit où se produit la suppression de publicité C3 et se termine à l’heure indiquée (plus courte ou plus longue que la période d’origine).

TVSDK fournit une `CustomRangesOpportunityGenerator` classe pour générer des opportunités de placement pour les plages MARK et DELETE. En mode REPLACE, TVSDK génère deux opportunités de placement pour chaque période :

* Le `CustomRangeResolver` système génère des opportunités de placement pour DELETE
* Le `AuditudeAdResolver` système génère des opportunités de placement pour INSERT.