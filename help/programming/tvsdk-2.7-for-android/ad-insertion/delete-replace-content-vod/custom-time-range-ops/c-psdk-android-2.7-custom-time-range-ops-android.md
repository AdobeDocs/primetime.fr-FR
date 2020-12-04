---
description: La classe CustomRangeMetadata identifie différents types de plages de temps dans un flux VOD, marqué, supprimé et remplacé. Pour chacun de ces types de plage de temps personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement de contenu publicitaire.
seo-description: La classe CustomRangeMetadata identifie différents types de plages de temps dans un flux VOD, marqué, supprimé et remplacé. Pour chacun de ces types de plage de temps personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement de contenu publicitaire.
seo-title: Opérations de plage de temps personnalisées
title: Opérations de plage de temps personnalisées
uuid: e9c6a135-124e-44d4-adf2-dc9d671e2483
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# Aperçu {#custom-time-range-operations}

La classe CustomRangeMetadata identifie différents types de plages de temps dans un flux VOD : marquer, supprimer et remplacer. Pour chacun de ces types de plage de temps personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement de contenu publicitaire.

<!--<a id="section_1323C0BAC259424C85A6ACFB48FE77EC"></a>-->

Pour la suppression et le remplacement des publicités, TVSDK utilise les modes *opération de plage de temps personnalisée* suivants :

* **** MARKTce mode était appelé marques publicitaires personnalisées dans les versions précédentes de TVSDK. Le mode marque les heures de début et de fin des publicités qui sont déjà placées dans le flux VOD. Lorsqu&#39;il y a des marqueurs de plage de temps de type `MARK` dans le flux, un emplacement initial de `Mode.MARK` est généré par `CustomMarkerOpportunityGenerator` et résolu par `CustomRangeResolver`. Aucune publicité n&#39;est insérée.

* **** DELETEFou  `DELETE` plages de temps, une initiale  `placementInformation` de type  `Mode.DELETE` est créée et résolue par  `CustomRangeResolver`. `DeleteRangeTimelineOperation` définit les plages à supprimer de la chronologie et TVSDK utilise  `removeByLocalTime` de l’API AVE (Adobe Video Engine) pour terminer cette opération. S’il existe des plages de DELETE et des métadonnées de prise de décision de publicité Adobe Primetime, ces plages sont d’abord supprimées, puis `AuditudeResolver` résout les publicités à l’aide du processus de prise de décision de publicité Adobe Primetime standard.

* **** REPLACEFou  `REPLACE` plages de temps, deux initiales  `placementInformations` sont créées, une  `Mode.DELETE` et une  `Mode.REPLACE`. `CustomRangeResolver` supprime d’abord les plages de temps, puis  `AuditudeResolver` insère les publicités de la plage spécifiée  `replaceDuration` dans la chronologie. Si aucun `replaceDuration` n&#39;est spécifié, le serveur détermine le contenu à insérer.

Pour prendre en charge ces opérations de plage de temps personnalisée, TVSDK fournit les éléments suivants :

* Résolveurs de contenu multiples

   Un flux peut comporter plusieurs résolveurs de contenu en fonction du mode de signalisation publicitaire et des métadonnées publicitaires. Le comportement change avec différentes combinaisons de modes de signalisation publicitaire et de métadonnées publicitaires.
* Plusieurs opportunités initiales à l&#39;aide de `CustomMarkerOpportunityGenerator`.
* Nouveau mode de signalisation de publicité, `CUSTOM_RANGES`.

   Les publicités sont placées en fonction des données de la période provenant d’une source externe, telle qu’un fichier JSON.

