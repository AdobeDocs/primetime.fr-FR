---
description: TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.
seo-description: TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.
seo-title: Opérations de plage de temps personnalisées
title: Opérations de plage de temps personnalisées
uuid: fb27f343-718d-444e-8fc1-5ae0be02557b
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# Aperçu {#custom-time-range-operations-overview}

TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.

La fonction de suppression et de remplacement étend la fonction de marques publicitaires personnalisées. Les marques publicitaires personnalisées désignent les sections du contenu principal comme des périodes de contenu liées à la publicité. Outre le marquage de ces plages de temps, vous pouvez également supprimer et remplacer des plages de temps.

<!--<a id="section_D3FE668CAF764DCC912373D5410C932C"></a>-->

La suppression et le remplacement des publicités sont implémentés avec des marqueurs personnalisés qui identifient différents types de plages de temps dans un flux VOD : marquer, supprimer et remplacer. Pour chaque période personnalisée, vous pouvez effectuer les opérations associées, y compris la suppression ou le remplacement de contenu publicitaire.

Pour la suppression et le remplacement des publicités, TVSDK inclut les modes *d’opération de plage de temps personnalisée* suivants :

* MARK - Distribue `AdBreak` événements pour les régions marquées. (Il s’appelait `customAdMarker` dans les versions précédentes de TVSDK.) L&#39;insertion de publicité n&#39;est pas autorisée dans ce mode.

* DELETE : pour ce mode, l’application utilise la classe `TimeRangeCollection` pour définir les régions temporelles de la suppression de publicité C3. L&#39;insertion de publicité est autorisée dans ce mode.
* REMPLACER - Dans ce mode, l’application remplace un `timeRange` par une décision d’annonce Adobe Primetime `AdBreak`. L’opération de remplacement début où se produit la suppression de publicité C3 et se termine à l’heure indiquée (plus courte ou plus longue que la période d’origine).

TVSDK fournit une classe `CustomRangesOpportunityGenerator` pour générer des opportunités de placement pour les plages MARK et DELETE. Pour le mode REPLACE, TVSDK génère deux opportunités de placement pour chaque période :

* Le `CustomRangeResolver` génère des opportunités de placement pour le DELETE
* Le `AuditudeAdResolver` génère des opportunités de placement pour INSERT.