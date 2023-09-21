---
description: Ces modifications apportées à l’API Android TVSDK prennent en charge la suppression et le remplacement des publicités.
title: Suppression et remplacement des publicités et modifications des API
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Suppression et remplacement des publicités et modifications des API{#ad-deletion-and-replacement-api-changes}

Ces modifications apportées à l’API Android TVSDK prennent en charge la suppression et le remplacement des publicités.

* `AdSignalingMode` Nouveau mode de signature de publicité de la période personnalisée

* `AdvertisingMetadata` Nouveau `setTimeRanges(TimeRangeCollection timeRanges, Metadata options)`: définit les périodes à marquer, supprimer ou remplacer lors du traitement des métadonnées.

* `ContentResolver`

   * Nouveau `public final boolean canResolve(PlacementOpportunity placementOpportunity)`
   * Nouveau `protected abstract boolean doCanResolve(PlacementOpportunity placementOpportunity)`

* Nouveau `ContentRemoval` class

  `TimelineOperation` qui définit la période à supprimer de la chronologie.

* `AuditudeResolver`

   * Nouveau `private LinkedList<AuditudeRequest> _requestQueue`
   * Nouveau `void startConsumer()`: commence à traiter la file d’attente des demandes de prise de décision et Primetime et s’assure que chaque demande est émise à l’adresse `MIN_INIT_REQUEST_INTERVAL` intervalles

   * Nouveau `processReplacementRange()`: extrait les périodes des métadonnées de publicité et génère `PlacementInformations`, et crée une requête de prise de décision publicitaire Primetime contenant le paramètre `PlacementInformations`.

   * Nouveau `canDoResolver()`: vérifie si l’opportunité d’emplacement contient des métadonnées de prise de décision publicitaire Primetime.

* Nouveau `CustomRangeHelper` Classe d’assistance qui extrait les métadonnées de période des métadonnées de publicité et supprime les sous-ensembles/recouvrements/plages de temps non valides.

* Nouveau `DeleteContentResolver` Résolveur de contenu qui résout les opportunités de référencement de `PlacementInformation.Mode.DELETE`

* Nouveau `NopTimelineOperation` Nouvelle opération de chronologie pour lorsqu’aucun remplacement ou emplacement de coupure publicitaire ne doit être effectué. Cette classe est utilisée pour faire la distinction entre cette erreur et lorsqu’une erreur se produit au cours du processus de résolution.

* `TimelineOperationQueue` Vérifie si l’opération de chronologie est une `NopTimelineOperation` avant traitement.

* `CustomAdMarkersContentResolver` Nouveau `canDoResolve()`: vérifie si une opportunité d’emplacement est de type `Mode.MARK`

* `MetadataResolver` Nouveau `canDoResolve()`: vérifie si une opportunité d’emplacement est de type `Mode.INSERT`

* `DefaultMetadataKeys` Nouveau `TIME_RANGES_METADATA_KEY("time_ranges_metadata_key")`

* `PlacementInformation`

   * Nouveau mode `enum (INSERT, DELETE, REPLACE, MARK)`
   * Nouveau type `CUSTOM_TIME_RANGES`

* `TimeRange` Nouveau `compareTo(TimeRange timeRange)`: peut ainsi trier les périodes en fonction de l’heure de début.

* Nouveau `ReplacementTimeRange` Étend le `TimeRange` qui représente une période de remplacement, avec une classe `begin`, `end`, et `replacement-duration` .

* `TimeRangeCollection`

   * Nouveau `MARK_RANGES, DELETE_RANGES, REPLACE_RANGES`
   * Renommé `CUSTOM_AD_MARKERS` to `MARK_RANGES`

   * Modifié `toMetadata(Metadata options)` pour placer des plages de suppression/marquage/remplacement dans les métadonnées de publicité.

* `MediaPlayerNotification`

   * Nouveau `UNDEFINED_TIME_RANGES`: lorsque le mode de signalisation de la publicité est Carte du serveur ou Code du manifeste et que les plages de remplacement figurent également dans les métadonnées de publicité, les plages de remplacement sont ignorées.
   * Nouveau `REPLACE_RANGES_NOT_AVAILABLE`: lorsqu’aucun mode de signalement de publicité n’est défini sur Plages de temps personnalisées et que les plages de remplacement ne sont pas disponibles, un avertissement est envoyé.

* `AdvertisingFactory` Nouveau `public abstract List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultAdvertisingFactory` Nouveau `public List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultContentResolverFactory` Nouveau `public static List<ContentResolver> createContentResolvers(MediaResource resource, Context context)`

* `DefaultMediaPlayer`

   * Dans `prepareToPlay()`: effectue une recherche initiale sur 0, car si la plage `[0,n]` est supprimé, le lecteur multimédia n’est pas lu automatiquement.

   * Dans `prepareToPlay()`: parcourt la liste des informations de placement initiales pour `mediaplayerclient` pour résoudre le problème.

   * Dans `extractAdSignalingMode()`: prise en charge du nouveau mode Période personnalisée.
   * Nouveau `private static List<PlacementInformation> createInitalPlacementInformations()`: génère les informations de placement initiales pour le mode de signalisation de la publicité et les résolveurs de contenu (dérivés des métadonnées de publicité).
   * Dans `ContentPlacementCompletedListener`: vérifie si `mediaPlayerClient` is `doneInitialResolving` avant d’appeler `endAdResolving`.

* `MediaPlayerClient`

   * Nouveau `List<ContentResolver> _contentResolvers`
   * Nouveau `int _reservations`
   * Nouveau `lookupContentResolver(PlacementOpportunity placementOpportunity)`: recherche le résolveur qui peut résoudre la variable `PlacementOpportunity`.

   * Modification du code pour créer plusieurs résolveurs de contenu.
   * Nouveau `public boolean doneInitialResolving()`: vérifie s’il reste des opportunités à résoudre.

* `VideoEngineTimeline`

   * Nouveau `removeContent(TimelineOperation timelineOperation)`: supprime une plage donnée de contenu de la chronologie.
   * Nouveau `removeContentByLocalTime(long begin, long end)`: supprime le contenu par heure locale donnée `begin` et `end`.

* `DefaultOpportunityDetectorFactory` Modifié `createOpportunityDetector`: pour les flux VOD, ne renvoyez qu’un nouveau `SpliceOutOpportunityDetector` s’il n’existe aucune plage MARK ou REPLACE (car ces plages ont la priorité sur le mode de signalement).
