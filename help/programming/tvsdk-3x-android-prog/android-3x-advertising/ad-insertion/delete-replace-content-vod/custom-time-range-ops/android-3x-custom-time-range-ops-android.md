---
description: La classe CustomRangeMetadata identifie différents types de plages de temps dans un flux VOD, marqué, supprimé et remplacé. Pour chacun de ces types de plage de temps personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement de contenu publicitaire.
seo-description: La classe CustomRangeMetadata identifie différents types de plages de temps dans un flux VOD, marqué, supprimé et remplacé. Pour chacun de ces types de plage de temps personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement de contenu publicitaire.
seo-title: Opérations de plage de temps personnalisées
title: Opérations de plage de temps personnalisées
uuid: eadd4d8d-0e03-40ca-ae3b-eede82bf2df8
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Opérations de plage de temps personnalisées {#custom-time-range-operations}

La classe CustomRangeMetadata identifie différents types de plages de temps dans un flux VOD : marquer, supprimer et remplacer. Pour chacun de ces types de plage de temps personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement de contenu publicitaire.

<!--<a id="section_1323C0BAC259424C85A6ACFB48FE77EC"></a>-->

Pour la suppression et le remplacement des publicités, TVSDK utilise les modes d’opération *de plage de temps* personnalisés suivants :

* **MARK** Ce mode était appelé marques publicitaires personnalisées dans les versions précédentes de TVSDK. Le mode marque les heures de début et de fin des publicités qui sont déjà placées dans le flux VOD. Lorsqu’il existe des marqueurs de plage de temps de type `MARK` dans le flux, un emplacement initial de `Mode.MARK` est généré par `CustomMarkerOpportunityGenerator` et résolu par `CustomRangeResolver`. Aucune publicité n&#39;est insérée.

* **SUPPRIMER** Pour `DELETE` les périodes, une initiale `placementInformation` de type `Mode.DELETE` est créée et résolue par `CustomRangeResolver`. `DeleteRangeTimelineOperation` définit les plages à supprimer de la chronologie et TVSDK utilise `removeByLocalTime` l’API Adobe Video Engine (AVE) pour terminer cette opération. S’il existe des plages de valeurs DELETE et des métadonnées de prise de décision publicitaire Adobe Primetime, elles sont d’abord supprimées, puis les publicités sont `AuditudeResolver` résolues à l’aide du processus de prise de décision publicitaire Adobe Primetime standard.

* **REMPLACER** Pour les `REPLACE` périodes, deux initiales `placementInformations` sont créées, une `Mode.DELETE` et une `Mode.REPLACE`. `CustomRangeResolver` supprime d’abord les plages de temps, puis `AuditudeResolver` insère les publicités de la plage spécifiée `replaceDuration` dans la chronologie. Si aucun `replaceDuration` paramètre n’est spécifié, le serveur détermine le contenu à insérer.

Pour prendre en charge ces opérations de plage de temps personnalisée, TVSDK fournit les éléments suivants :

* Résolveurs de contenu multiples

   Un flux peut comporter plusieurs résolveurs de contenu en fonction du mode de signalisation publicitaire et des métadonnées publicitaires. Le comportement change avec différentes combinaisons de modes de signalisation publicitaire et de métadonnées publicitaires.
* Plusieurs opportunités initiales utilisant `CustomMarkerOpportunityGenerator`.
* Un nouveau mode de signalisation publicitaire, `CUSTOM_RANGES`.

   Les publicités sont placées en fonction des données de la période provenant d’une source externe, telle qu’un fichier JSON.