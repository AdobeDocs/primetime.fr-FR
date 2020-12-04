---
description: Ces modifications dans TVSDK prennent en charge la suppression et le remplacement des annonces.
seo-description: Ces modifications dans TVSDK prennent en charge la suppression et le remplacement des annonces.
seo-title: Modifications de l’API de suppression et de remplacement des publicités
title: Modifications de l’API de suppression et de remplacement des publicités
uuid: 9d208d3b-6459-4aaf-bc56-53c405ccc1b6
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# Modifications de l&#39;API de suppression et de remplacement des publicités {#ad-deletion-and-replacement-api-changes}

Ces modifications dans TVSDK prennent en charge la suppression et le remplacement des annonces.

* `AdSignalingMode` Mode  `CUSTOM_RANGES` de signalisation Ajouté.

* `OpportunityGenerator`  `extractAdSignalingMode()` - Défini  `AdSignalingMode.CUSTOM_RANGES` si les plages de remplacement figurent dans les métadonnées.

* `PlacementType`  `CUSTOM_RANGE` type Ajouté.

* `PlacementMode`

   * Mode `DELETE` Ajouté.
   * Mode `MARK` Ajouté
   * Mode `FreeReplace` Ajouté - Ce mode a une durée mais est une insertion pure.

* `TimeRange` Ne plus être une  `final` classe

* Méthode `ReplaceTimeRange()` Ajoutée

   Étend `TimeRange` pour avoir une propriété `replacementDuration`. Pour les cas MARK et DELETE, `replacementDuration` est 0.

* `TimeRangeCollection`

   * Fonction utilitaire `toReplaceMetadata()` Ajoutée pour extraire `timeRanges`.

   * Modifié pour fonctionner avec `DELETE` et `REPLACE`

   * `METADATA_KEY_CUSTOM_MARK_RANGES`,  `METADATA_KEY_CUSTOM_DELETE_RANGES`,  `METADATA_KEY_CUSTOM_REPLACE_RANGES`

* `CatalogItem`

   * `createCustomTimeRangesFrom()` Ajouté : crée des métadonnées pour les cas d’utilisation de MARK/DELETE/REPLACE à partir du fichier JSON.
   * Supprimé `createCustomAdMarkersMetadataFrom()`

* `DefaultMetadataKeys`

   * `CUSTOM_DELETE_RANGES_METADATA_KEY` Ajouté
   * `CUSTOM_REPLACE_RANGES_METADATA_KEY` Ajouté
   * `CUSTOM_AD_MARKERS_METADATA_KEY` (n’a pas changé)

* `DefaultContentFactory`

   * `doRetrieveGenerators()`

      * `CustomRangesOpportunityGenerator` Ajouté lorsque les métadonnées contiennent des plages personnalisées
   * `doRetrieveResolvers()`

      * Ajouter `CustomRangeResolver` pour le moment où les plages personnalisées DELETE et REMPLACER sont présentes dans les métadonnées
      * Déplacé `CustomAdMarkerResolver` devant `AuditudeResolver`


* `CustomRangeOpportunityGenerator` Ajouté

   * `doUpdate()` Laisser vide - aucune mise à jour, VOD
   * `doProcess()` Crée un emplacement de nouveau type  `Placement.Delete_Range`

   * Ajouté `CustomRangeOppotunityGenerator` en haut de la liste des générateurs dans `DefaultContentFactory`, les plages de suppression sont donc traitées avant les insertions publicitaires.

   * Ajouté `createCustomRangeOpportunities` pour créer toutes les opportunités

      MARK - Une opportunité pour chaque plage de marques valide de `PlacementType.CUSTOM_RANGE` et `PlacementMode.MARK`

      DELETE - Une opportunité pour chaque plage de suppression valide de `PlacementType.CUSTOM_RANGE` et `PlacementMode.DELETE`

      REMPLACE - Deux opportunités pour chaque plage de remplacement valide :

      1. Une opportunité de suppression de plage de `PlacementType.CUSTOM_RANGE` et `PlacementMode.DELETE`.

      1. Une opportunité de prise de décision et de prise de décision Primetime de `PlacementType.MID_ROLL` ou `PlacementType.PRE_ROLL` et `PlacementMode.FREEREPLACE`

* `CustomRangeResolver` Ajouté :

   * `doCanResolve()` renvoie  `true` pour les plages de suppression.

   * Ajouté `createDeleteRangeOperation()` pour créer `DeleteRange` pour le placement

* `CustomRangeHelper` Ajouté :

   * Classe d&#39;utilitaire commune permettant d&#39;extraire Mark/Delete/Replace `timeRanges` et de les traiter.
   * `extractCustomRangesMetadata()` Ajouté
   * `extractCustomRanges()` Ajouté
   * `mergeRanges()` Ajouté : résout les conflits et les sous-ensembles/fusions

* `MediaPlayerTimeline`:

   * &quot;>Dans `executeOperation()`, si l&#39;opération est `DeleteRange`, un appel a été ajouté pour supprimer la méthode dans l&#39;opération.

   * Dans `executeOperation()`, si l&#39;opération est `NOPTimelineOperation` (vide `AdBreaks` revenant du serveur), un appel a été ajouté pour effacer.

   * `onDeleteRangeComplete()` Ajouté
   * `removeRange()` Ajouté
   * Dans `adjustPlacement()`, pour le mode `PlacementMode.FREEREPLACE`, la durée a été mise à zéro. Cette durée est nécessaire plus tôt lors de la demande de `AdBreaks`, à ce stade, elle doit être égale à zéro pour être une insertion pure.

* `VideoEngineTimeline` Ajouté  `removeC3Ad()` - appel  `removeByLocalTime()` pour supprimer des plages

* `AdSignalingModeGenerator`

   * `doConfigure()` - Ne pas résoudre si aucune opportunité n&#39;est générée
   * `createInitialOpportunity()` - Ne pas générer d&#39;opportunité initiale pour  `AdSignalingMode.CUSTOM_RANGE`. Le document `CustomRangeOpportunityGenerator` couvre déjà cette question.

* `DeleteRange`

   * Étend `TimelineOperation`.
   * Créé par `CustomRangeResolver` pour la suppression et le remplacement (la partie de suppression du remplacement)

* `AuditudeConstant`

   * `MAX_PLACEMENTS_PER_REQUEST 1->5` - autoriser l&#39;emballage
   * `MINIMUM_AD_DURATION 10->5`

* `AuditudeRequest` La  `accepts()` méthode a été modifiée pour permettre l&#39;emballage de différents types de placement (pré-roulage, mid-roll, post-roll).

* `AuditudeRequestHelper` Correctifs de bogues permettant le remplacement des paramètres d’annonce par le serveur

* `AuditudeResolver` La  `canBePacked()` méthode a été modifiée pour autoriser l&#39;emballage.

* `CustomAdResolver` Les fonctions  `timeRange` d&#39;extraction ont été supprimées. Nous obtenons un emplacement à la fois, et transformons cela en `AdBreakPlacement timelineOperation`.

