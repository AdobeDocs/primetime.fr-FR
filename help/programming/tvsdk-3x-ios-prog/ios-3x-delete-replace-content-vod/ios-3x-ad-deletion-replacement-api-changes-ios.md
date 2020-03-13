---
description: TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.
seo-description: TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.
seo-title: Modifications de l’API de suppression et de remplacement des publicités
title: Modifications de l’API de suppression et de remplacement des publicités
uuid: 3689d31f-4feb-4ea5-ac49-ef2e71472f4b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Modifications de l’API de suppression et de remplacement des publicités {#ad-deletion-and-replacement-api-changes}

TVSDK prend en charge la suppression et le remplacement programmatiques du contenu publicitaire dans les flux VOD.

La fonction de suppression et de remplacement étend la fonction des marqueurs publicitaires personnalisés. Les marqueurs publicitaires personnalisés marquent les sections du contenu principal comme des périodes de contenu liées aux publicités. Outre le marquage de ces plages de temps, vous pouvez également supprimer et remplacer des plages de temps.

<!--<a id="section_7A90BFE99F1A4D908D6DDB0B49FA1199"></a>-->

Les modifications suivantes ont été apportées à la prise en charge et au remplacement de TVSDK.

**Nouvelles API**

* `PTTimeRangeCollection` est une classe publique qui définit un ensemble prédéfini de plages et un type :

   * `property PTTimeRangeCollectionType type` indique le type de période.
   * `property NSArray* ranges` sert à définir les plages de temps.

      Le type d’objet attendu dans le tableau est `PTReplacementTimeRange` ou `CMTimeRange`.

      >[!TIP]
      >
      >Tous les objets du tableau doivent être du même type.

   * `PTTimeRangeCollectionType` est un énumérateur qui définit le comportement des plages définies dans la variable `PTTimeRangeCollection`:

      * `PTTimeRangeCollectionTypeMarkRanges`: Le type des plages est *Mark*. Les plages servent à marquer les plages du contenu comme des publicités.

      * `PTTimeRangeCollectionTypeDeleteRanges`: Le type des plages est Supprimer. Les plages définies sont supprimées du contenu principal avant l’insertion de la publicité.
      * `PTTimeRangeCollectionTypeReplaceRanges`: Le type des plages est Remplacer. Les plages définies sont remplacées à partir de l’élément principal par des publicités (le mode de signalisation publicitaire est défini sur `PTAdSignalingModeCustomTimeRanges`).

* `PTReplacementTimeRange` - Nouvelle classe publique qui définit une plage unique de `PTTimeRangeCollection`:

   * `property CMTimeRange range` - Définit la  et la durée de la plage.
   * `property long replacementDuration` - Si le type de la `TimeRangeCollection` variable est `PTTimeRangeCollectionTypeReplaceRanges`, la `replacementDuration` variable est utilisée pour créer une opportunité de placement (insertion publicitaire) d’une durée de `replacementDuration`. Si le paramètre `replacementDuration` n’est pas défini, le serveur d’annonces détermine la durée et le nombre de publicités pour cette opportunité d’emplacement.

* `PTAdSignalingMode`:

   * `PTAdSignalingModeCustomTimeRanges` - Ajout d’un nouveau type de `PTAdSignalingMode`. Ce mode est utilisé conjointement avec le `PTTimeRangeCollection` type avec `PTTimeRangeCollectionReplace` pour l’insertion d’annonces publicitaires en fonction des plages de remplacement.

* `PTAdMetadata`:

   * `property PTTimeRangeCollection* timeRangeCollection` - Pour définir les plages de temps utilisées dans les plages de marques, de suppressions et de remplacements dans le contenu de lecture.

* Journaux d’avertissement :

   * `UNDEFINED_TIME_RANGES`

      * Type - Avertissement
      * Description : le mode de signalisation de la publicité est défini comme des plages personnalisées, mais les plages personnalisées ne sont pas définies.
   * `INVALID_TIME_RANGES`

      * Type - Avertissement
      * Description - Une ou plusieurs plages de temps ne sont pas valides et seront ignorées ou modifiées.


**API obsolètes**

* `PTAdMetadata`:

   * `property NSArray* externalAdRanges` - Cette propriété a été précédemment utilisée pour définir des plages C3 pour le marquage. Elle est désormais obsolète, car ces plages sont définies via `PTTimeRangeCollection`.