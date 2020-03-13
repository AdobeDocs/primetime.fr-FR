---
description: Ces modifications dans la prise en charge et la suppression et le remplacement de TVSDK.
seo-description: Ces modifications dans la prise en charge et la suppression et le remplacement de TVSDK.
seo-title: Modifications de l’API de suppression et de remplacement des publicités
title: Modifications de l’API de suppression et de remplacement des publicités
uuid: 9d208d3b-6459-4aaf-bc56-53c405ccc1b6
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Modifications de l’API de suppression et de remplacement des publicités {#ad-deletion-and-replacement-api-changes}

Ces modifications dans la prise en charge et la suppression et le remplacement de TVSDK.

* `AdSignalingMode` Ajout du mode `CUSTOM_RANGES` de signalisation.

* `OpportunityGenerator`  `extractAdSignalingMode()` - Définissez `AdSignalingMode.CUSTOM_RANGES` si les plages de remplacement figurent dans les métadonnées.

* `PlacementType` Ajout d’un `CUSTOM_RANGE` type.

* `PlacementMode`

   * Ajout `DELETE` du mode.
   * Mode `MARK` ajouté
   * Mode ajouté `FreeReplace` : ce mode a une durée mais est une insertion pure

* `TimeRange` N’est plus une `final` classe

* Ajout d’une `ReplaceTimeRange()` méthode

   Etend `TimeRange` à avoir une `replacementDuration` propriété. Pour les cas MARK et DELETE, `replacementDuration` la valeur est 0.

* `TimeRangeCollection`

   * Ajout de `toReplaceMetadata()` la fonction utilitaire à extraire `timeRanges`.

   * Modifié pour travailler avec `DELETE` et `REPLACE`

   * `METADATA_KEY_CUSTOM_MARK_RANGES`, `METADATA_KEY_CUSTOM_DELETE_RANGES`, `METADATA_KEY_CUSTOM_REPLACE_RANGES`

* `CatalogItem`

   * Ajout `createCustomTimeRangesFrom()` : crée des métadonnées pour les cas d’utilisation de MARK/DELETE/REPLACE à partir du fichier JSON.
   * Supprimé `createCustomAdMarkersMetadataFrom()`

* `DefaultMetadataKeys`

   * Ajout `CUSTOM_DELETE_RANGES_METADATA_KEY`
   * Ajout `CUSTOM_REPLACE_RANGES_METADATA_KEY`
   * `CUSTOM_AD_MARKERS_METADATA_KEY` (n’a pas changé)

* `DefaultContentFactory`

   * `doRetrieveGenerators()`

      * Ajouté `CustomRangesOpportunityGenerator` pour le moment où les métadonnées contiennent des plages personnalisées
   * `doRetrieveResolvers()`

      * Ajouter `CustomRangeResolver` pour le moment où les plages personnalisées DELETE et REPLACE sont présentes dans les métadonnées
      * Avancée `CustomAdMarkerResolver` devant `AuditudeResolver`


* Ajout `CustomRangeOpportunityGenerator`

   * `doUpdate()` Laisse vide - aucune mise à jour, VOD
   * `doProcess()` Crée un nouvel emplacement d’un nouveau type `Placement.Delete_Range`

   * Ajouté `CustomRangeOppotunityGenerator` au haut du des générateurs dans `DefaultContentFactory`, les plages de suppression sont donc traitées avant les insertions publicitaires.

   * Ajout `createCustomRangeOpportunities` de toutes les opportunités

      MARQUE - Une opportunité pour chaque plage de marques valide `PlacementType.CUSTOM_RANGE` et `PlacementMode.MARK`

      DELETE - Une opportunité pour chaque plage de suppression valide `PlacementType.CUSTOM_RANGE` et `PlacementMode.DELETE`

      REMPLACE - Deux opportunités pour chaque période de remplacement valide :

      1. Une opportunité de suppression de plage de `PlacementType.CUSTOM_RANGE` et `PlacementMode.DELETE`.

      1. Une opportunité de prise de décision publicitaire Primetime `PlacementType.MID_ROLL` ou `PlacementType.PRE_ROLL` et `PlacementMode.FREEREPLACE`

* Ajout `CustomRangeResolver`:

   * `doCanResolve()` renvoie `true` pour les plages de suppression.

   * Ajout `createDeleteRangeOperation()` à la création `DeleteRange` pour le placement

* Ajout `CustomRangeHelper`:

   * Classe d’utilitaire commune permettant d’extraire Mark/Delete/Replace `timeRanges` et de les traiter.
   * Ajout `extractCustomRangesMetadata()`
   * Ajout `extractCustomRanges()`
   * Ajout `mergeRanges()` - Résout les conflits et les sous-ensembles/fusions

* `MediaPlayerTimeline`:

   * &quot;>Dans `executeOperation()`le cas où l&#39;opération est `DeleteRange`, ajout d&#39;un appel pour supprimer la méthode dans l&#39;opération

   * Dans `executeOperation()`, si l’opération est `NOPTimelineOperation` (vide `AdBreaks` revenant du serveur), ajout d’un appel à effacer.

   * Ajout `onDeleteRangeComplete()`
   * Ajout `removeRange()`
   * En `adjustPlacement()`mode `PlacementMode.FREEREPLACE` , la durée a été mise à zéro. Cette durée est nécessaire plus tôt lors de la demande `AdBreaks`, à ce stade, elle doit être égale à zéro pour être une insertion pure.

* `VideoEngineTimeline` Ajout `removeC3Ad()` - appel `removeByLocalTime()` pour supprimer des plages

* `AdSignalingModeGenerator`

   * `doConfigure()` - Ne pas résoudre si aucune opportunité n&#39;est générée
   * `createInitialOpportunity()` - Ne pas générer d&#39;opportunité initiale pour `AdSignalingMode.CUSTOM_RANGE`. Le `CustomRangeOpportunityGenerator` couvre déjà.

* `DeleteRange`

   * Étend `TimelineOperation`.
   * Créé par `CustomRangeResolver` pour suppression et remplacement (partie de suppression du remplacement)

* `AuditudeConstant`

   * `MAX_PLACEMENTS_PER_REQUEST 1->5` - autoriser l&#39;emballage
   * `MINIMUM_AD_DURATION 10->5`

* `AuditudeRequest` La `accepts()` méthode a été modifiée pour permettre l&#39;emballage de différents types de placement (pré-roulage, milieu, post-roulage).

* `AuditudeRequestHelper` Correctifs pour autoriser le remplacement des paramètres d’annonce par le serveur

* `AuditudeResolver` La `canBePacked()` méthode a été modifiée pour autoriser l&#39;emballage

* `CustomAdResolver` Les fonctions   ont été supprimées. `timeRange` On obtient un emplacement à la fois, et on en fait un `AdBreakPlacement timelineOperation`.

