---
description: La classe CustomRangeMetadata identifie différents types de plages temporelles dans un flux VOD, que vous marquez, supprimez ou remplacez. Pour chacun de ces types de période personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement du contenu publicitaire.
title: Opérations de période personnalisées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Opérations de période personnalisées {#custom-time-range-operations}

La classe CustomRangeMetadata identifie différents types de plages dans un flux VOD : marquage, suppression et remplacement. Pour chacun de ces types de période personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement du contenu publicitaire.

<!--<a id="section_1323C0BAC259424C85A6ACFB48FE77EC"></a>-->

Pour la suppression et le remplacement des publicités, TVSDK utilise les éléments suivants : *opération de période personnalisée* modes :

* **MARQUE** Ce mode était appelé marqueurs publicitaires personnalisés dans les versions précédentes de TVSDK. Le mode marque les heures de début et de fin pour les publicités déjà placées dans le flux VOD. Lorsqu’il existe des marqueurs de période de type `MARK` dans le flux, un emplacement initial de `Mode.MARK` est généré par `CustomMarkerOpportunityGenerator` et résolus par `CustomRangeResolver`. Aucune publicité n’est insérée.

* **DELETE** Pour `DELETE` périodes, une période initiale `placementInformation` de type `Mode.DELETE` est créé et résolu par `CustomRangeResolver`. `DeleteRangeTimelineOperation` définit les plages à supprimer de la chronologie ; TVSDK utilise `removeByLocalTime` à partir de l’API Adobe Video Engine (AVE) pour terminer cette opération. S’il existe des plages de DELETE et des métadonnées de prise de décision publicitaire Adobe Primetime, elles sont d’abord supprimées, puis la variable `AuditudeResolver` résout les publicités à l’aide du processus de prise de décision publicitaire standard d’Adobe Primetime.

* **REMPLACER** Pour `REPLACE` plages horaires, deux plages initiales `placementInformations` sont créés, un `Mode.DELETE` et un `Mode.REPLACE`. `CustomRangeResolver` supprime d’abord les périodes, puis la fonction `AuditudeResolver` insère les publicités du `replaceDuration` dans la chronologie. Si non `replaceDuration` est spécifié, le serveur détermine les éléments à insérer.

Pour prendre en charge ces opérations de période personnalisées, TVSDK fournit les éléments suivants :

* Résolveurs de contenu multiples

  Un flux peut comporter plusieurs résolveurs de contenu en fonction du mode de signalisation de la publicité et des métadonnées de publicité. Le comportement change avec différentes combinaisons de modes de signal publicitaire et de métadonnées publicitaires.
* Plusieurs opportunités initiales utilisant `CustomMarkerOpportunityGenerator`.
* un nouveau mode de signalisation des publicités, `CUSTOM_RANGES`.

  Les publicités sont placées en fonction des données de période d’une source externe, telle qu’un fichier JSON.
