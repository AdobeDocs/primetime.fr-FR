---
description: Ces modifications apportées à la prise en charge et au remplacement de TVSDK prennent en charge la suppression et le remplacement des publicités.
title: Suppression et remplacement des publicités et modifications des API
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Suppression et remplacement des publicités et modifications des API {#ad-deletion-and-replacement-api-changes}

Ces modifications apportées à la prise en charge et au remplacement de TVSDK prennent en charge la suppression et le remplacement des publicités.

* `AdSignalingMode` Ajout `CUSTOM_RANGES` mode de signalétique.

* `OpportunityGenerator`  `extractAdSignalingMode()` - Set `AdSignalingMode.CUSTOM_RANGES` si les plages de remplacement figurent dans les métadonnées.

* `PlacementType` Ajout `CUSTOM_RANGE` type.

* `PlacementMode`

   * Ajout `DELETE` mode .
   * Ajout `MARK` mode
   * Ajout `FreeReplace` mode : ce mode a une durée, mais il s’agit d’une insertion pure.

* `TimeRange` N’est plus `final` class

* Ajout `ReplaceTimeRange()` method

  Étend `TimeRange` pour disposer d’un `replacementDuration` . Pour les cas MARK et DELETE, `replacementDuration` est 0.

* `TimeRangeCollection`

   * Ajout `toReplaceMetadata()` fonction utilitaire à extraire `timeRanges`.

   * Modifié pour travailler avec `DELETE` et `REPLACE`

   * `METADATA_KEY_CUSTOM_MARK_RANGES`, `METADATA_KEY_CUSTOM_DELETE_RANGES`, `METADATA_KEY_CUSTOM_REPLACE_RANGES`

* `CatalogItem`

   * Ajout `createCustomTimeRangesFrom()` - Crée des métadonnées pour les cas d’utilisation MARK/DELETE/REPLACE à partir du fichier JSON.
   * Supprimé `createCustomAdMarkersMetadataFrom()`

* `DefaultMetadataKeys`

   * Ajout `CUSTOM_DELETE_RANGES_METADATA_KEY`
   * Ajout `CUSTOM_REPLACE_RANGES_METADATA_KEY`
   * `CUSTOM_AD_MARKERS_METADATA_KEY` (n’a pas changé)

* `DefaultContentFactory`

   * `doRetrieveGenerators()`

      * Ajout `CustomRangesOpportunityGenerator` pour les cas où les métadonnées contiennent des plages personnalisées

   * `doRetrieveResolvers()`

      * Ajouter `CustomRangeResolver` pour les cas où des plages personnalisées de DELETE et de REMPLACEMENT sont présentes dans les métadonnées
      * Déplacé `CustomAdMarkerResolver` devant `AuditudeResolver`

* Ajout `CustomRangeOpportunityGenerator`

   * `doUpdate()` Laisse vide - pas de mise à jour, VOD
   * `doProcess()` Crée un emplacement de nouveau type `Placement.Delete_Range`

   * Ajout `CustomRangeOppotunityGenerator` en haut de la liste des groupes électrogènes dans `DefaultContentFactory`, les plages de suppression sont donc traitées avant les insertions publicitaires.

   * Ajout `createCustomRangeOpportunities` créer toutes les opportunités

     MARK - Une opportunité pour chaque plage de marques valide `PlacementType.CUSTOM_RANGE` et `PlacementMode.MARK`

     DELETE : une opportunité pour chaque plage de suppression valide `PlacementType.CUSTOM_RANGE` et `PlacementMode.DELETE`

     REPLACE - Deux opportunités pour chaque période de remplacement valide :

      1. Une opportunité de suppression de plage `PlacementType.CUSTOM_RANGE` et `PlacementMode.DELETE`.

      1. Une opportunité publicitaire Primetime de prise de décision publicitaire `PlacementType.MID_ROLL` ou `PlacementType.PRE_ROLL` et `PlacementMode.FREEREPLACE`

* Ajout `CustomRangeResolver`:

   * `doCanResolve()` renvoie `true` pour les plages de suppression.

   * Ajout `createDeleteRangeOperation()` pour créer `DeleteRange` pour l’emplacement

* Ajout `CustomRangeHelper`:

   * Classe d’utilitaire commune pour extraire Mark/Delete/Replace `timeRanges` et les traiter.
   * Ajout `extractCustomRangesMetadata()`
   * Ajout `extractCustomRanges()`
   * Ajout `mergeRanges()` - Résout les conflits et les sous-ensembles/fusions

* `MediaPlayerTimeline`:

   * &quot;>Dans `executeOperation()`, si l’opération est `DeleteRange`, ajout d’un appel pour supprimer la méthode dans l’opération.

   * Dans `executeOperation()`, si l’opération est `NOPTimelineOperation` (vide) `AdBreaks` revenant du serveur), ajout d’un appel à effacer.

   * Ajout `onDeleteRangeComplete()`
   * Ajout `removeRange()`
   * Dans `adjustPlacement()`, pour `PlacementMode.FREEREPLACE` , la durée a été désactivée. Cette durée est nécessaire plus tôt lorsque vous demandez `AdBreaks`, à ce stade, il doit être nul pour être une insertion pure.

* `VideoEngineTimeline` Ajout `removeC3Ad()` - call `removeByLocalTime()` pour les plages de suppression

* `AdSignalingModeGenerator`

   * `doConfigure()` - Ne pas résoudre si aucune opportunité n’est générée
   * `createInitialOpportunity()` - Ne pas générer d’opportunité initiale pour `AdSignalingMode.CUSTOM_RANGE`. La variable `CustomRangeOpportunityGenerator` couvre déjà ceci.

* `DeleteRange`

   * Étend `TimelineOperation`.
   * Créé par `CustomRangeResolver` pour la suppression et le remplacement (partie &quot;suppression&quot; du remplacement)

* `AuditudeConstant`

   * `MAX_PLACEMENTS_PER_REQUEST 1->5` - autoriser le conditionnement
   * `MINIMUM_AD_DURATION 10->5`

* `AuditudeRequest` La variable `accepts()` a été modifiée afin de permettre l’emballage de différents types d’emplacement (preroll, mid-roll, post-roll).

* `AuditudeRequestHelper` Correctifs de bogues permettant le remplacement des paramètres de publicité par le serveur

* `AuditudeResolver` La variable `canBePacked()` a été modifiée pour autoriser le conditionnement.

* `CustomAdResolver` La variable `timeRange` les fonctions d’extraction ont été supprimées. On obtient un emplacement à la fois et on le transforme en un `AdBreakPlacement timelineOperation`.
