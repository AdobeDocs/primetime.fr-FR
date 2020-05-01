---
description: Ces modifications dans TVSDK prennent en charge la suppression et le remplacement des annonces.
seo-description: Ces modifications dans TVSDK prennent en charge la suppression et le remplacement des annonces.
seo-title: Modifications de l’API de suppression et de remplacement des publicités
title: Modifications de l’API de suppression et de remplacement des publicités
uuid: 9d208d3b-6459-4aaf-bc56-53c405ccc1b6
translation-type: tm+mt
source-git-commit: ''

---


# Modifications de l’API de suppression et de remplacement des publicités {#ad-deletion-and-replacement-api-changes}

Ces modifications dans TVSDK prennent en charge la suppression et le remplacement des annonces.

* `AdSignalingMode` Ajout du mode `CUSTOM_RANGES` de signalisation.

* `OpportunityGenerator`  `extractAdSignalingMode()` - Définissez `AdSignalingMode.CUSTOM_RANGES` si les plages de remplacement figurent dans les métadonnées.

* `PlacementType` Ajout d’un `CUSTOM_RANGE` type.

* `PlacementMode`

   * Ajout `DELETE` du mode.
   * Ajout `MARK` du mode
   * Ajout `FreeReplace` du mode - Ce mode a une durée mais est une insertion pure

* `TimeRange` N&#39;est plus une `final` classe

* Ajout d’une `ReplaceTimeRange()` méthode

   Etend `TimeRange` à avoir une `replacementDuration` propriété. Pour les cas MARK et DELETE, `replacementDuration` la valeur est 0.

* `TimeRangeCollection`

   * Ajout de la fonction `toReplaceMetadata()` utilitaire à extraire `timeRanges`.

   * Modifié pour travailler avec `DELETE` et `REPLACE`

   * `METADATA_KEY_CUSTOM_MARK_RANGES`, `METADATA_KEY_CUSTOM_DELETE_RANGES`, `METADATA_KEY_CUSTOM_REPLACE_RANGES`

* `CatalogItem`

   * Ajout `createCustomTimeRangesFrom()` - Crée des métadonnées pour les cas d’utilisation de MARK/DELETE/REPLACE à partir du fichier JSON.
   * Supprimé `createCustomAdMarkersMetadataFrom()`

* `DefaultMetadataKeys`

   * Ajout `CUSTOM_DELETE_RANGES_METADATA_KEY`
   * Ajout `CUSTOM_REPLACE_RANGES_METADATA_KEY`
   * `CUSTOM_AD_MARKERS_METADATA_KEY` (n’a pas changé)

* `DefaultContentFactory`

   * `doRetrieveGenerators()`

      * Ajout `CustomRangesOpportunityGenerator` pour le moment où les métadonnées contiennent des plages personnalisées
   * `doRetrieveResolvers()`

      * Ajouter `CustomRangeResolver` pour le moment où les plages personnalisées DELETE et REPLACE sont présentes dans les métadonnées
      * Avancée `CustomAdMarkerResolver` devant `AuditudeResolver`


* Ajout `CustomRangeOpportunityGenerator`

   * `doUpdate()` Laisser vide - aucune mise à jour, VOD
   * `doProcess()` Crée un emplacement de nouveau type `Placement.Delete_Range`

   * Ajout `CustomRangeOppotunityGenerator` au haut de la liste des générateurs dans `DefaultContentFactory`, de sorte que les plages de suppression sont traitées avant les insertions publicitaires.

   * Ajout `createCustomRangeOpportunities` pour créer toutes les opportunités

      MARK - Une opportunité pour chaque plage de marques valide `PlacementType.CUSTOM_RANGE` et `PlacementMode.MARK`

      DELETE - Une opportunité pour chaque plage de suppression valide `PlacementType.CUSTOM_RANGE` et `PlacementMode.DELETE`

      REMPLACE - Deux opportunités pour chaque plage de remplacement valide :

      1. Une opportunité de suppression de plage de `PlacementType.CUSTOM_RANGE` et `PlacementMode.DELETE`.

      1. Une opportunité de prise de décision publicitaire Primetime `PlacementType.MID_ROLL` ou `PlacementType.PRE_ROLL` et `PlacementMode.FREEREPLACE`

* Ajout `CustomRangeResolver`:

   * `doCanResolve()` renvoie `true` pour les plages de suppression.

   * Ajout `createDeleteRangeOperation()` à la création `DeleteRange` du placement

* Ajout `CustomRangeHelper`:

   * Classe d’utilitaire commune permettant d’extraire Mark/Delete/Replace `timeRanges` et de les traiter.
   * Ajout `extractCustomRangesMetadata()`
   * Ajout `extractCustomRanges()`
   * Ajout `mergeRanges()` - Résout les conflits et les sous-ensembles/fusions

* `MediaPlayerTimeline`:

   * &quot;>Dans `executeOperation()`, si l&#39;opération est `DeleteRange`effectuée, ajout d&#39;un appel pour supprimer la méthode dans l&#39;opération.

   * Dans `executeOperation()`, si l’opération est `NOPTimelineOperation` (vide `AdBreaks` revenant du serveur), ajout d’un appel à effacer.

   * Ajout `onDeleteRangeComplete()`
   * Ajout `removeRange()`
   * Dans `adjustPlacement()`le cas du `PlacementMode.FREEREPLACE` mode, la durée a été décalée. Cette durée est nécessaire plus tôt lors de la demande `AdBreaks`, à ce stade, elle doit être égale à zéro pour être pure insertion.

* `VideoEngineTimeline` Ajout `removeC3Ad()` - appel `removeByLocalTime()` pour supprimer des plages

* `AdSignalingModeGenerator`

   * `doConfigure()` - Ne pas résoudre si aucune opportunité n&#39;est générée
   * `createInitialOpportunity()` - Ne pas générer d&#39;opportunité initiale pour `AdSignalingMode.CUSTOM_RANGE`. Le `CustomRangeOpportunityGenerator` livre couvre déjà cela.

* `DeleteRange`

   * Étend `TimelineOperation`.
   * Créé par `CustomRangeResolver` pour suppression et remplacement (partie de suppression du remplacement)

* `AuditudeConstant`

   * `MAX_PLACEMENTS_PER_REQUEST 1->5` - autoriser l&#39;emballage
   * `MINIMUM_AD_DURATION 10->5`

* `AuditudeRequest` La `accepts()` méthode a été modifiée pour permettre l&#39;emballage de différents types de placement (pré-roulage, mid-roll, post-roll).

* `AuditudeRequestHelper` Correctifs de bogues permettant le remplacement des paramètres d’annonce par le serveur

* `AuditudeResolver` La `canBePacked()` méthode a été modifiée pour autoriser l&#39;emballage.

* `CustomAdResolver` Les fonctions `timeRange` d&#39;extraction ont été supprimées. On obtient un placement à la fois, et on en fait un `AdBreakPlacement timelineOperation`.

