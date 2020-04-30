---
description: Ces modifications dans l’API TVSDK Android prennent en charge la suppression et le remplacement des annonces.
seo-description: Ces modifications dans l’API TVSDK Android prennent en charge la suppression et le remplacement des annonces.
seo-title: Modifications de l’API de suppression et de remplacement des publicités
title: Modifications de l’API de suppression et de remplacement des publicités
uuid: 2bb8a331-6851-4442-99de-b01500a0e1e2
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Modifications de l’API de suppression et de remplacement des publicités{#ad-deletion-and-replacement-api-changes}

Ces modifications dans l’API TVSDK Android prennent en charge la suppression et le remplacement des annonces.

* `AdSignalingMode` Nouveau mode personnalisé de signature publicitaire de la période

* `AdvertisingMetadata` Nouveau `setTimeRanges(TimeRangeCollection timeRanges, Metadata options)`: Définit les plages de temps à marquer, supprimer ou remplacer lors du traitement des métadonnées.

* `ContentResolver`

   * Nouveau `public final boolean canResolve(PlacementOpportunity placementOpportunity)`
   * Nouveau `protected abstract boolean doCanResolve(PlacementOpportunity placementOpportunity)`

* Nouvelle `ContentRemoval` classe

   `TimelineOperation` classe qui définit la période à supprimer du plan de montage chronologique

* `AuditudeResolver`

   * Nouveau `private LinkedList<AuditudeRequest> _requestQueue`
   * Nouveau `void startConsumer()`: Débuts traitant la file d’attente des demandes de décision et de prise de décision Primetime et s’assurant que chaque demande est émise à `MIN_INIT_REQUEST_INTERVAL` intervalles

   * Nouveau `processReplacementRange()`: Extrait les plages de temps des métadonnées de la publicité et les génère `PlacementInformations`et crée une demande de prise de décision publicitaire Primetime contenant le `PlacementInformations`.

   * Nouveau `canDoResolver()`: Vérifie si l&#39;opportunité de placement contient des métadonnées Primetime de prise de décision publicitaire

* Nouvelle classe `CustomRangeHelper` Helper qui extrait les métadonnées de plage de temps des métadonnées publicitaires et supprime les sous-ensembles/recouvrements/plages de temps non valides.

* Nouveau `DeleteContentResolver` résolveur de contenu qui résout les opportunités d&#39;emplacement de `PlacementInformation.Mode.DELETE`

* Nouvelle `NopTimelineOperation` opération de chronologie pour les cas où aucun placement ou remplacement de coupure publicitaire n’est nécessaire. Cette classe permet de distinguer entre cette variable et lorsqu’une erreur se produit au cours du processus de résolution.

* `TimelineOperationQueue` Vérifie si l&#39;opération de chronologie est une opération `NopTimelineOperation` avant traitement.

* `CustomAdMarkersContentResolver` Nouveau `canDoResolve()`: Vérifie si une opportunité de placement est de type `Mode.MARK`

* `MetadataResolver` Nouveau `canDoResolve()`: Vérifie si une opportunité de placement est de type `Mode.INSERT`

* `DefaultMetadataKeys` Nouveau `TIME_RANGES_METADATA_KEY("time_ranges_metadata_key")`

* `PlacementInformation`

   * Nouveau mode `enum (INSERT, DELETE, REPLACE, MARK)`
   * Nouveau type `CUSTOM_TIME_RANGES`

* `TimeRange` Nouveau `compareTo(TimeRange timeRange)`: Vous pouvez donc trier les plages de dates en fonction de l’heure de début.

* New `ReplacementTimeRange` Étend la `TimeRange` classe qui représente une plage de temps de remplacement, avec un `begin`, `end`et `replacement-duration` paramètre.

* `TimeRangeCollection`

   * Nouveau `MARK_RANGES, DELETE_RANGES, REPLACE_RANGES`
   * Renommé `CUSTOM_AD_MARKERS` en `MARK_RANGES`

   * Modifié `toMetadata(Metadata options)` pour insérer des plages de suppression/marquage/remplacement dans les métadonnées publicitaires.

* `MediaPlayerNotification`

   * Nouveau `UNDEFINED_TIME_RANGES`: Lorsque le mode de signalisation de la publicité est Carte du serveur ou Cotes du manifeste et que les plages de remplacement figurent également dans les métadonnées de la publicité, les plages de remplacement sont ignorées.
   * Nouveau `REPLACE_RANGES_NOT_AVAILABLE`: Lorsque le mode de signalisation publicitaire est Plages de temps personnalisées et Plages de remplacement non disponibles, un avertissement est envoyé.

* `AdvertisingFactory` Nouveau `public abstract List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultAdvertisingFactory` Nouveau `public List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultContentResolverFactory` Nouveau `public static List<ContentResolver> createContentResolvers(MediaResource resource, Context context)`

* `DefaultMediaPlayer`

   * Dans `prepareToPlay()`: Effectue une recherche initiale sur 0, car si la plage `[0,n]` est supprimée, le lecteur de médias ne sera pas lu automatiquement.

   * Dans `prepareToPlay()`: Permet de parcourir la liste des informations de placement initiales à `mediaplayerclient` résoudre.

   * Dans `extractAdSignalingMode()`: Prise en charge du nouveau mode de plage de temps personnalisée.
   * Nouveau `private static List<PlacementInformation> createInitalPlacementInformations()`: Génère les informations de placement initiales pour le mode de signalisation de la publicité et les résolveurs de contenu (dérivés des métadonnées de la publicité).
   * Dans `ContentPlacementCompletedListener`: Vérifie si `mediaPlayerClient` est `doneInitialResolving` avant d&#39;appeler `endAdResolving`.

* `MediaPlayerClient`

   * Nouveau `List<ContentResolver> _contentResolvers`
   * Nouveau `int _reservations`
   * Nouveau `lookupContentResolver(PlacementOpportunity placementOpportunity)`: Recherche quel résolveur peut résoudre le `PlacementOpportunity`.

   * Modification du code pour créer plusieurs résolveurs de contenu.
   * Nouveau `public boolean doneInitialResolving()`: Vérifie s&#39;il reste des possibilités à résoudre.

* `VideoEngineTimeline`

   * Nouveau `removeContent(TimelineOperation timelineOperation)`: Supprime une plage donnée de contenu du plan de montage chronologique.
   * Nouveau `removeContentByLocalTime(long begin, long end)`: Supprime le contenu par heure locale donnée `begin` et `end`.

* `DefaultOpportunityDetectorFactory` Modifié `createOpportunityDetector`: Pour les flux VOD, ne renvoyez un nouveau `SpliceOutOpportunityDetector` si aucune plage MARK ou REPLACE n’existe (car ces plages ont la priorité sur le mode de signalisation).

