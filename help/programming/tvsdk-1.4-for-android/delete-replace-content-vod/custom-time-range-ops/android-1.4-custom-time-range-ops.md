---
description: TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.
seo-description: TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.
seo-title: Opérations de plage de temps personnalisées
title: Opérations de plage de temps personnalisées
uuid: e04af786-8dac-41a6-8406-f2ca04f612a4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---


# Opérations de plage de temps personnalisée {#custom-time-range-operations}

TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.

La fonction de suppression et de remplacement étend la fonction de marques publicitaires personnalisées. Les marques publicitaires personnalisées désignent les sections du contenu principal comme des périodes de contenu liées à la publicité. Outre le marquage de ces plages de temps, vous pouvez également supprimer et remplacer des plages de temps.

La suppression et le remplacement des publicités sont implémentés avec des éléments `TimeRange` qui identifient différents types de plages de temps dans un flux VOD : marquer, supprimer et remplacer. Pour chacun de ces types de plage de temps personnalisés, vous pouvez effectuer les opérations correspondantes, y compris la suppression et le remplacement de contenu publicitaire.

Pour la suppression et le remplacement des publicités, TVSDK utilise les modes *opération de plage de temps personnalisée* suivants :

* **MARK**
 (ces marques étaient appelées marques publicitaires personnalisées dans les versions précédentes de TVSDK). Ils marquent les heures de début et de fin pour les publicités qui sont déjà placées dans le flux VOD. Lorsqu’il existe des marqueurs de plage de temps de type MARK dans le flux, un emplacement initial de 
`Mode.MARK` est générée et résolue par le  `CustomAdMarkersContentResolver`. Aucune publicité n&#39;est insérée.

* **Plages de temps**
DELETEF ou DELETE, une plage initiale 
`placementInformation` de type  `Mode.DELETE` est créé et résolu par le  `DeleteContentResolver`code correspondant. `ContentRemoval` est un nouveau  `timelineOperation` qui définit les plages à supprimer du plan de montage chronologique. TVSDK utilise `removeByLocalTime` de l’API AVE (Adobe Video Engine) pour faciliter cette opération. S’il existe des plages de DELETE et des métadonnées de prise de décision de publicité Adobe Primetime (précédemment connues sous le nom d’Auditude), les plages sont d’abord supprimées, puis `AuditudeResolver` résout les publicités à l’aide du processus de prise de décision de publicité Adobe Primetime standard.

* ****
REPLACEF ou PLACER des plages de temps, deux plages initiales 
`placementInformations` sont créés, un  `Mode.DELETE` et un  `Mode.REPLACE`. `DeleteContentResolver` supprime d&#39;abord les plages de temps, puis `AuditudeResolver` insère les publicités de `replaceDuration` dans la chronologie. Si aucun `replaceDuration` n&#39;est spécifié, le serveur détermine le contenu à insérer.

Pour prendre en charge ces opérations de plage de temps personnalisée, TVSDK fournit les éléments suivants :

* Résolveurs de contenu multiples

   Un flux peut comporter plusieurs résolveurs de contenu en fonction du mode de signalisation publicitaire et des métadonnées publicitaires. Le comportement change avec différentes combinaisons de modes de signalisation publicitaire et de métadonnées publicitaires.
* Plusieurs `PlacementInformations` initiales `DefaultMediaPlayer` créent une liste de `PlacementInformations` initiales en fonction du mode de signalisation de la publicité et des métadonnées publicitaires à résoudre par `MediaPlayerClient`.

* Nouveau mode de signalisation publicitaire : Plages de temps personnalisées

   Les publicités sont placées en fonction des données de la période provenant d’une source externe (par exemple, un fichier JSON).