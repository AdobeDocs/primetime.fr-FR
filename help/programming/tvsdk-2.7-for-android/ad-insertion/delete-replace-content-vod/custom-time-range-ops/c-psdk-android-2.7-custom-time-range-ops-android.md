---
description: La classe CustomRangeMetadata identifie différents types de plages de temps dans un flux VOD, qui marque, supprime et remplace. Pour chacun de ces types de période personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement du contenu de la publicité.
seo-description: La classe CustomRangeMetadata identifie différents types de plages de temps dans un flux VOD, qui marque, supprime et remplace. Pour chacun de ces types de période personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement du contenu de la publicité.
seo-title: Opérations de plage de temps personnalisées
title: Opérations de plage de temps personnalisées
uuid: e9c6a135-124e-44d4-adf2-dc9d671e2483
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Présentation {#custom-time-range-operations}

La classe CustomRangeMetadata identifie différents types de plages de temps dans un flux VOD : marquer, supprimer et remplacer. Pour chacun de ces types de période personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement du contenu de la publicité.

<!--<a id="section_1323C0BAC259424C85A6ACFB48FE77EC"></a>-->

Pour la suppression et le remplacement des publicités, TVSDK utilise les modes *personnalisés d’opération* de plage de temps suivants :

* **MARQUE** Ce mode était appelé marques publicitaires personnalisées dans les versions précédentes de TVSDK. Le mode indique les heures de début et de fin des publicités qui sont déjà placées dans le flux VOD. Lorsqu’il existe des marqueurs de plage de temps de type `MARK` dans le flux, un emplacement initial de `Mode.MARK` est généré par `CustomMarkerOpportunityGenerator` et résolu par `CustomRangeResolver`. Aucune publicité n’est insérée.

* **SUPPRIMER** Pour les `DELETE` périodes, une initiale `placementInformation` de type `Mode.DELETE` est créée et résolue par `CustomRangeResolver`. `DeleteRangeTimelineOperation` définit les plages à supprimer du plan de montage chronologique et TVSDK les utilise `removeByLocalTime` à partir de l’API Adobe Video Engine (AVE) pour terminer cette opération. S’il existe des plages DELETE et des métadonnées de prise de décision publicitaire Adobe Primetime, elles sont d’abord supprimées, puis les publicités `AuditudeResolver` sont résolues à l’aide du processus de prise de décision publicitaire Adobe Primetime classique.

* **REMPLACER** Pour les `REPLACE` périodes, deux initiales `placementInformations` sont créées, une `Mode.DELETE` et une `Mode.REPLACE`. `CustomRangeResolver` supprime d’abord les plages de temps, puis `AuditudeResolver` insère les publicités du paramètre spécifié `replaceDuration` dans le plan de montage chronologique. Si aucun `replaceDuration` paramètre n’est spécifié, le serveur détermine le contenu à insérer.

Pour prendre en charge ces opérations de plage de temps personnalisée, TVSDK fournit les éléments suivants :

* Résolveurs de contenu multiples

   Un flux peut comporter plusieurs résolveurs de contenu en fonction du mode de signalisation de la publicité et des métadonnées de la publicité. Le comportement change avec différentes combinaisons de modes de signalisation et de métadonnées publicitaires.
* Plusieurs opportunités initiales utilisant `CustomMarkerOpportunityGenerator`.
* Un nouveau mode de signalisation publicitaire, `CUSTOM_RANGES`.

   Les publicités sont placées sur la base des données de la période provenant d’une source externe, telle qu’un fichier JSON.

