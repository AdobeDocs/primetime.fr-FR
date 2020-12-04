---
description: Les modifications suivantes dans TVSDK prennent en charge la suppression et le remplacement des annonces.
seo-description: Les modifications suivantes dans TVSDK prennent en charge la suppression et le remplacement des annonces.
seo-title: Modifications de l’API de suppression et de remplacement des publicités
title: Modifications de l’API de suppression et de remplacement des publicités
uuid: 7cc50e7a-666f-4588-9c16-ad6d7d75cb65
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# Modifications de l&#39;API de suppression et de remplacement des publicités{#ad-deletion-and-replacement-api-changes}

Les modifications suivantes dans TVSDK prennent en charge la suppression et le remplacement des annonces.

**Nouvelles API**

* `PTTimeRangeCollection` est une classe publique qui définit un ensemble prédéfini de plages et un type :

   * `property PTTimeRangeCollectionType type` indique le type de période.
   * `property NSArray* ranges` sert à définir les plages de temps.

      Le type d&#39;objet attendu dans le tableau est `PTReplacementTimeRange` ou `CMTimeRange`.

      >[!TIP]
      >
      >Tous les objets du tableau doivent être du même type.

   * `PTTimeRangeCollectionType` est un enum qui définit le comportement des plages définies dans le  `PTTimeRangeCollection`:

      * `PTTimeRangeCollectionTypeMarkRanges`: Le type des plages est  *Mark*. Les plages servent à marquer les plages du contenu en tant que publicités.

      * `PTTimeRangeCollectionTypeDeleteRanges`: Le type des plages est Supprimer. Les plages définies sont supprimées du contenu principal avant l’insertion de la publicité.
      * `PTTimeRangeCollectionTypeReplaceRanges`: Le type des plages est Remplacer. Les plages définies sont remplacées à partir de l’élément principal par des publicités (le mode de signalisation publicitaire est défini sur `PTAdSignalingModeCustomTimeRanges`).

* `PTReplacementTimeRange` - Nouvelle classe publique qui définit une plage unique de  `PTTimeRangeCollection`:

   * `property CMTimeRange range` - Définit le début et la durée de la plage.
   * `property long replacementDuration` - Si le type de la  `TimeRangeCollection` est  `PTTimeRangeCollectionTypeReplaceRanges`, la  `replacementDuration` est utilisée pour créer une opportunité de placement (insertion publicitaire) avec une durée de  `replacementDuration`. Si `replacementDuration` n&#39;est pas défini, le serveur d&#39;annonces détermine la durée et le nombre de publicités pour cette opportunité d&#39;emplacement.

* `PTAdSignalingMode`:

   * `PTAdSignalingModeCustomTimeRanges` - Ajouté un nouveau type de  `PTAdSignalingMode`. Ce mode est utilisé conjointement avec le `PTTimeRangeCollection` avec le type `PTTimeRangeCollectionReplace` pour l&#39;insertion d&#39;annonces publicitaires en fonction des plages de remplacement.

* `PTAdMetadata`:

   * `property PTTimeRangeCollection* timeRangeCollection` - Pour définir les plages de temps utilisées dans les plages de marques, de suppressions et de remplacements dans le contenu de lecture.

* Journaux d’avertissement :

   * `UNDEFINED_TIME_RANGES`

      * Type - Avertissement
      * Description - Le mode de signalisation de la publicité est défini comme des plages personnalisées mais les plages personnalisées ne sont pas définies.
   * `INVALID_TIME_RANGES`

      * Type - Avertissement
      * Description : une ou plusieurs plages de dates ne sont pas valides et seront ignorées ou modifiées.


**API obsolètes**

* `PTAdMetadata`:

   * `property NSArray* externalAdRanges` - Cette propriété a été précédemment utilisée pour définir des plages C3 pour le marquage. Elle est désormais obsolète, car ces plages sont définies via `PTTimeRangeCollection`.

