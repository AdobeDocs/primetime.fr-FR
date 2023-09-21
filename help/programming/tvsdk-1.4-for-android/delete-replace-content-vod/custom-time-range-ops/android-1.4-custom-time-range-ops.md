---
description: TVSDK prend en charge la suppression et le remplacement programmatiques de contenu publicitaire dans les flux VOD.
title: Opérations de période personnalisées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Opérations de période personnalisées {#custom-time-range-operations}

TVSDK prend en charge la suppression et le remplacement programmatiques de contenu publicitaire dans les flux VOD.

La fonction de suppression et de remplacement étend la fonction de marqueurs d’annonce personnalisés. Les marqueurs de publicité personnalisés marquent les sections du contenu principal comme des périodes de contenu liées à la publicité. Outre le marquage de ces plages temporelles, vous pouvez également supprimer et remplacer des plages temporelles.

La suppression et le remplacement des publicités sont implémentés avec `TimeRange` éléments qui identifient différents types de périodes dans un flux VOD : marquer, supprimer et remplacer. Pour chacun de ces types de période personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement du contenu publicitaire.

Pour la suppression et le remplacement des publicités, TVSDK utilise les éléments suivants : *opération de période personnalisée* modes :

* **MARQUE**
(Ils étaient appelés marqueurs publicitaires personnalisés dans les versions précédentes de TVSDK). Ils marquent les heures de début et de fin pour les publicités déjà placées dans le flux VOD. Lorsqu’il existe des marqueurs de période de type MARK dans le flux, un emplacement initial de `Mode.MARK` est généré et résolu par la variable `CustomAdMarkersContentResolver`. Aucune publicité n’est insérée.

* **DELETE**
Pour les périodes DELETE, une `placementInformation` de type `Mode.DELETE` est créé et résolu par le `DeleteContentResolver`. `ContentRemoval` est un nouveau `timelineOperation` qui définit les plages à supprimer de la chronologie. Utilisation de TVSDK `removeByLocalTime` à partir de l’API Adobe Video Engine (AVE) pour faciliter cette opération. S’il existe des plages de DELETE et des métadonnées de prise de décision publicitaire Adobe Primetime (précédemment connues sous le nom d’Auditude), elles sont d’abord supprimées, puis la variable `AuditudeResolver` résout les publicités à l’aide du processus de prise de décision publicitaire Adobe Primetime normal.

* **REMPLACER**
Pour les périodes REPLACE, deux périodes initiales `placementInformations` sont créés, un `Mode.DELETE` et un `Mode.REPLACE`. La variable `DeleteContentResolver` supprime d’abord les périodes, puis la fonction `AuditudeResolver` insère les publicités du `replaceDuration` dans la chronologie. Si non `replaceDuration` est spécifié, le serveur détermine les éléments à insérer.

Pour prendre en charge ces opérations de période personnalisées, TVSDK fournit les éléments suivants :

* Résolveurs de contenu multiples

  Un flux peut comporter plusieurs résolveurs de contenu en fonction du mode de signalisation de la publicité et des métadonnées de publicité. Le comportement change avec différentes combinaisons de modes de signal publicitaire et de métadonnées publicitaires.
* Initial multiple `PlacementInformations` La variable `DefaultMediaPlayer` crée une liste de valeurs initiales `PlacementInformations` en fonction du mode de signalisation de la publicité et des métadonnées de publicité à résoudre par le `MediaPlayerClient`.

* Nouveau mode de signalisation des publicités : plages de dates personnalisées

  Les publicités sont placées en fonction des données de période d’une source externe (par exemple, un fichier JSON).
