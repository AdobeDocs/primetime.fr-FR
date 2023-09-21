---
description: TVSDK prend en charge la suppression et le remplacement programmatiques de contenu publicitaire dans les flux VOD.
title: Suppression et remplacement des publicités et modifications des API
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# Suppression et remplacement des publicités et modifications des API {#ad-deletion-and-replacement-api-changes}

TVSDK prend en charge la suppression et le remplacement programmatiques de contenu publicitaire dans les flux VOD.

La fonction de suppression et de remplacement étend la fonction de marqueurs d’annonce personnalisés. Les marqueurs de publicité personnalisés marquent les sections du contenu principal comme des périodes de contenu liées à la publicité. Outre le marquage de ces plages temporelles, vous pouvez également supprimer et remplacer des plages temporelles.

<!--<a id="section_7A90BFE99F1A4D908D6DDB0B49FA1199"></a>-->

Les modifications suivantes apportées à TVSDK prennent en charge la suppression et le remplacement des publicités.

**Nouvelles API**

* `PTTimeRangeCollection` est une classe publique qui définit un ensemble prédéfini de plages et un type :

   * `property PTTimeRangeCollectionType type` indique le type de période.
   * `property NSArray* ranges` sert à définir les périodes.

     Les types d’objets attendus dans le tableau sont les suivants : `PTReplacementTimeRange` ou `CMTimeRange`.

     >[!TIP]
     >
     >Tous les objets du tableau doivent être du même type.

   * `PTTimeRangeCollectionType` est une énumération qui définit le comportement des plages définies dans la variable `PTTimeRangeCollection`:

      * `PTTimeRangeCollectionTypeMarkRanges`: les plages sont de type *Marquer*. Les plages servent à marquer les plages du contenu comme des publicités.

      * `PTTimeRangeCollectionTypeDeleteRanges`: les plages sont de type Supprimer. Les plages définies sont supprimées du contenu principal avant l’insertion de publicités.
      * `PTTimeRangeCollectionTypeReplaceRanges`: les plages sont de type Remplacer. Les plages définies sont remplacées à partir de l’emplacement principal par des publicités (le mode de signalisation de la publicité est défini sur `PTAdSignalingModeCustomTimeRanges`).

* `PTReplacementTimeRange` - Nouvelle classe publique qui définit une seule plage de la variable `PTTimeRangeCollection`:

   * `property CMTimeRange range` - Définit le début et la durée de la plage.
   * `property long replacementDuration` - Si le type de la variable `TimeRangeCollection` is `PTTimeRangeCollectionTypeReplaceRanges`, la variable `replacementDuration` est utilisé pour créer une opportunité d’emplacement (insertion de publicités) avec une durée `replacementDuration`. Si la variable `replacementDuration` n’est pas définie, le serveur d’annonces détermine la durée et le nombre de publicités pour cette opportunité d’emplacement.

* `PTAdSignalingMode`:

   * `PTAdSignalingModeCustomTimeRanges` - Ajout d’un nouveau type de `PTAdSignalingMode`. Ce mode est utilisé conjointement avec la fonction `PTTimeRangeCollection` avec type `PTTimeRangeCollectionReplace` pour l’insertion d’annonces en fonction des plages de remplacement.

* `PTAdMetadata`:

   * `property PTTimeRangeCollection* timeRangeCollection` - Pour définir les plages d’heures utilisées dans les plages de marquage/suppression/remplacement du contenu de lecture.

* Logs d&#39;avertissement :

   * `UNDEFINED_TIME_RANGES`

      * Type - Avertissement
      * Description : le mode de signalisation de la publicité est défini comme des plages personnalisées, mais les plages personnalisées ne sont pas définies.

   * `INVALID_TIME_RANGES`

      * Type - Avertissement
      * Description : une ou plusieurs plages de dates ne sont pas valides et seront ignorées ou modifiées.

**API obsolètes**

* `PTAdMetadata`:

   * `property NSArray* externalAdRanges` - Cette propriété était auparavant utilisée pour définir des plages C3 pour le marquage. Elle est désormais obsolète, car ces plages sont définies via `PTTimeRangeCollection`.
