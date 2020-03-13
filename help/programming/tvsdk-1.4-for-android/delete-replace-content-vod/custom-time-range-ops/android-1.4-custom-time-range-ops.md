---
description: TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.
seo-description: TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.
seo-title: Opérations de plage de temps personnalisées
title: Opérations de plage de temps personnalisées
uuid: e04af786-8dac-41a6-8406-f2ca04f612a4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Opérations de plage de temps personnalisées {#custom-time-range-operations}

TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.

La fonction de suppression et de remplacement étend la fonction des marqueurs publicitaires personnalisés. Les marqueurs publicitaires personnalisés marquent les sections du contenu principal comme des périodes de contenu liées aux publicités. Outre le marquage de ces plages de temps, vous pouvez également supprimer et remplacer des plages de temps.

La suppression et le remplacement des publicités sont implémentés avec `TimeRange` des éléments qui identifient différents types de plages de temps dans un flux VOD : marquer, supprimer et remplacer. Pour chacun de ces types de période personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement du contenu de la publicité.

Pour la suppression et le remplacement des publicités, TVSDK utilise les modes *personnalisés d’opération* de plage de temps suivants :

* **MARK**(Ces marques étaient appelées marques publicitaires personnalisées dans les versions précédentes de TVSDK). Ils marquent les heures de début et de fin des publicités qui sont déjà placées dans le flux VOD. Lorsqu’il existe des marqueurs de plage de temps de type MARK dans le flux, un emplacement initial de `Mode.MARK` est généré et résolu par le `CustomAdMarkersContentResolver`. Aucune publicité n’est insérée.

* **SUPPRIMER** Pour les plages de temps SUPPRIMER, une initiale `placementInformation` de type `Mode.DELETE` est créée et résolue par la `DeleteContentResolver`valeur correspondante. `ContentRemoval` est un nouveau `timelineOperation` qui définit les plages à supprimer du plan de montage chronologique. TVSDK utilise `removeByLocalTime` l’API Adobe Video Engine (AVE) pour faciliter cette opération. S’il existe des plages DELETE et des métadonnées de prise de décision publicitaire Adobe Primetime (précédemment connues sous le nom d’Auditude), les plages sont d’abord supprimées, puis les publicités `AuditudeResolver` sont résolues à l’aide du processus normal de prise de décision et de prévisualisation Adobe Primetime.

* **REMPLACER** Pour les plages de temps REMPLACER, deux plages initiales `placementInformations` sont créées, une `Mode.DELETE` et une `Mode.REPLACE`. Le `DeleteContentResolver` programme supprime d’abord les plages de temps, puis `AuditudeResolver` insère les publicités du groupe spécifié `replaceDuration` dans le plan de montage chronologique. Si aucun `replaceDuration` paramètre n’est spécifié, le serveur détermine le contenu à insérer.

Pour prendre en charge ces opérations de plage de temps personnalisée, TVSDK fournit les éléments suivants :

* Résolveurs de contenu multiples

   Un flux peut comporter plusieurs résolveurs de contenu en fonction du mode de signalisation de la publicité et des métadonnées de la publicité. Le comportement change avec différentes combinaisons de modes de signalisation et de métadonnées publicitaires.
* Initiale multiple `PlacementInformations` Le `DefaultMediaPlayer` crée un de la valeur initiale `PlacementInformations` en fonction du mode de signalisation de la publicité et des métadonnées publicitaires à résoudre par le `MediaPlayerClient`.

* Nouveau mode de signalisation publicitaire : Plages de temps personnalisées

   Les publicités sont placées sur la base des données de la période provenant d’une source externe (fichier JSON, par exemple).