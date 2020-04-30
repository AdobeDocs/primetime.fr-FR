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

La fonction de suppression et de remplacement étend la fonction de marques publicitaires personnalisées. Les marques publicitaires personnalisées désignent les sections du contenu principal comme des périodes de contenu liées à la publicité. Outre le marquage de ces plages de temps, vous pouvez également supprimer et remplacer des plages de temps.

La suppression et le remplacement des publicités sont implémentés avec `TimeRange` des éléments qui identifient différents types de plages de temps dans un flux VOD : marquer, supprimer et remplacer. Pour chacun de ces types de plage de temps personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement de contenu publicitaire.

Pour la suppression et le remplacement des publicités, TVSDK utilise les modes d’opération *de plage de temps* personnalisés suivants :

* **MARK**(ces marques étaient appelées marques publicitaires personnalisées dans les versions précédentes de TVSDK). Ils marquent les heures de début et de fin pour les publicités qui sont déjà placées dans le flux VOD. Lorsqu’il existe des marqueurs de plage de temps de type MARK dans le flux, un emplacement initial de `Mode.MARK` est généré et résolu par le `CustomAdMarkersContentResolver`. Aucune publicité n&#39;est insérée.

* **SUPPRIMER** Pour les plages de temps DELETE, une initiale `placementInformation` de type `Mode.DELETE` est créée et résolue par la `DeleteContentResolver`liste correspondante. `ContentRemoval` est un nouveau `timelineOperation` qui définit les plages à supprimer du plan de montage chronologique. TVSDK utilise `removeByLocalTime` l’API Adobe Video Engine (AVE) pour faciliter cette opération. S’il existe des plages de valeurs DELETE et des métadonnées de prise de décision publicitaire Adobe Primetime (précédemment connues sous le nom d’Auditude), les plages sont d’abord supprimées, puis les publicités sont `AuditudeResolver` résolues à l’aide du processus normal de prise de décision publicitaire Adobe Primetime.

* **REMPLACER** Pour les plages de temps REMPLACER, deux plages de temps initiales `placementInformations` sont créées, une `Mode.DELETE` et une `Mode.REPLACE`. Le `DeleteContentResolver` programme supprime d&#39;abord les plages de temps, puis `AuditudeResolver` insère les publicités de la période spécifiée `replaceDuration` dans la chronologie. Si aucun `replaceDuration` paramètre n’est spécifié, le serveur détermine le contenu à insérer.

Pour prendre en charge ces opérations de plage de temps personnalisée, TVSDK fournit les éléments suivants :

* Résolveurs de contenu multiples

   Un flux peut comporter plusieurs résolveurs de contenu en fonction du mode de signalisation publicitaire et des métadonnées publicitaires. Le comportement change avec différentes combinaisons de modes de signalisation publicitaire et de métadonnées publicitaires.
* Plusieurs initiales `PlacementInformations` Le `DefaultMediaPlayer` crée une liste de initiales `PlacementInformations` en fonction du mode de signalisation de la publicité et des métadonnées publicitaires à résoudre par le `MediaPlayerClient`serveur.

* Nouveau mode de signalisation publicitaire : Plages de temps personnalisées

   Les publicités sont placées en fonction des données de la période provenant d’une source externe (par exemple, un fichier JSON).