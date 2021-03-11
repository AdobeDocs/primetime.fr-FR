---
description: Ces modifications dans l’API TVSDK Android prennent en charge la suppression et le remplacement des annonces.
title: Modifications de l’API de suppression et de remplacement des publicités
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# Modifications de l&#39;API de suppression et de remplacement des publicités{#ad-deletion-and-replacement-api-changes}

Ces modifications dans l’API TVSDK Android prennent en charge la suppression et le remplacement des annonces.

* `AdSignalingMode` Nouveau mode personnalisé de signature publicitaire de la période

* `AdvertisingMetadata` Nouveau  `setTimeRanges(TimeRangeCollection timeRanges, Metadata options)`: Définit les plages de temps à marquer, supprimer ou remplacer lors du traitement des métadonnées.

* `ContentResolver`

   * Nouveau `public final boolean canResolve(PlacementOpportunity placementOpportunity)`
   * Nouveau `protected abstract boolean doCanResolve(PlacementOpportunity placementOpportunity)`

* Nouvelle classe `ContentRemoval`

   `TimelineOperation` classe qui définit la période à supprimer du plan de montage chronologique

* `AuditudeResolver`

   * Nouveau `private LinkedList<AuditudeRequest> _requestQueue`
   * Nouveau `void startConsumer()` : Débuts qui traitent la file d’attente des demandes de décision et de prise de décision Primetime et s’assurent que chaque demande est émise à `MIN_INIT_REQUEST_INTERVAL` intervalles

   * Nouveau `processReplacementRange()` : Extrait les plages de temps des métadonnées de la publicité et génère `PlacementInformations`, puis crée une demande de prise de décision publicitaire Primetime contenant le `PlacementInformations`.

   * Nouveau `canDoResolver()` : Vérifie si l&#39;opportunité de placement contient des métadonnées Primetime de prise de décision publicitaire

* Nouvelle classe d&#39;assistance `CustomRangeHelper` qui extrait les métadonnées de plage de temps des métadonnées publicitaires et supprime les sous-ensembles/recouvrements/plages de temps non valides.

* Nouvel outil de résolution de contenu `DeleteContentResolver` qui résout les opportunités de positionnement de `PlacementInformation.Mode.DELETE`

* Nouvelle `NopTimelineOperation` nouvelle opération de chronologie pour les cas où aucun placement ou remplacement de coupure publicitaire ne doit être effectué. Cette classe permet de distinguer entre cette variable et lorsqu’une erreur se produit au cours du processus de résolution.

* `TimelineOperationQueue` Vérifie si l&#39;opération de chronologie est une opération  `NopTimelineOperation` avant traitement.

* `CustomAdMarkersContentResolver` Nouveau  `canDoResolve()`: Vérifie si une opportunité de placement est de type  `Mode.MARK`

* `MetadataResolver` Nouveau  `canDoResolve()`: Vérifie si une opportunité de placement est de type  `Mode.INSERT`

* `DefaultMetadataKeys` Nouveau  `TIME_RANGES_METADATA_KEY("time_ranges_metadata_key")`

* `PlacementInformation`

   * Nouveau mode `enum (INSERT, DELETE, REPLACE, MARK)`
   * Nouveau type `CUSTOM_TIME_RANGES`

* `TimeRange` Nouveau  `compareTo(TimeRange timeRange)`: Vous pouvez donc trier les plages de dates en fonction de l’heure de début.

* New `ReplacementTimeRange` Étend la classe `TimeRange` qui représente une plage de temps de remplacement, avec un paramètre `begin`, `end` et `replacement-duration`.

* `TimeRangeCollection`

   * Nouveau `MARK_RANGES, DELETE_RANGES, REPLACE_RANGES`
   * Renommé `CUSTOM_AD_MARKERS` en `MARK_RANGES`

   * Modifié `toMetadata(Metadata options)` pour insérer des plages delete/mark/replace dans les métadonnées publicitaires.

* `MediaPlayerNotification`

   * Nouveau `UNDEFINED_TIME_RANGES` : Lorsque le mode de signalisation de la publicité est Carte du serveur ou Cotes du manifeste et que les plages de remplacement figurent également dans les métadonnées de la publicité, les plages de remplacement sont ignorées.
   * Nouveau `REPLACE_RANGES_NOT_AVAILABLE` : Lorsque le mode de signalisation publicitaire est Plages de temps personnalisées et Plages de remplacement non disponibles, un avertissement est envoyé.

* `AdvertisingFactory` Nouveau  `public abstract List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultAdvertisingFactory` Nouveau  `public List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultContentResolverFactory` Nouveau  `public static List<ContentResolver> createContentResolvers(MediaResource resource, Context context)`

* `DefaultMediaPlayer`

   * Dans `prepareToPlay()` : Effectue une recherche initiale sur 0, car si la plage `[0,n]` est supprimée, le lecteur de médias ne sera pas lu automatiquement.

   * Dans `prepareToPlay()` : Permet de parcourir la liste des informations de placement initiales que `mediaplayerclient` doit résoudre.

   * Dans `extractAdSignalingMode()` : Prise en charge du nouveau mode de plage de temps personnalisée.
   * Nouveau `private static List<PlacementInformation> createInitalPlacementInformations()` : Génère les informations de placement initiales pour le mode de signalisation de la publicité et les résolveurs de contenu (dérivés des métadonnées de la publicité).
   * Dans `ContentPlacementCompletedListener` : Vérifie si `mediaPlayerClient` est `doneInitialResolving` avant d&#39;appeler `endAdResolving`.

* `MediaPlayerClient`

   * Nouveau `List<ContentResolver> _contentResolvers`
   * Nouveau `int _reservations`
   * Nouveau `lookupContentResolver(PlacementOpportunity placementOpportunity)` : Recherche quel résolveur peut résoudre le `PlacementOpportunity`.

   * Modification du code pour créer plusieurs résolveurs de contenu.
   * Nouveau `public boolean doneInitialResolving()` : Vérifie s&#39;il reste des possibilités à résoudre.

* `VideoEngineTimeline`

   * Nouveau `removeContent(TimelineOperation timelineOperation)` : Supprime une plage donnée de contenu du plan de montage chronologique.
   * Nouveau `removeContentByLocalTime(long begin, long end)` : Supprime le contenu par heure locale donnée `begin` et `end`.

* `DefaultOpportunityDetectorFactory` Modifié  `createOpportunityDetector`: Pour les flux VOD, ne renvoyez une nouvelle valeur que  `SpliceOutOpportunityDetector` s’il n’existe aucune plage MARK ou REPLACE (car ces plages ont la priorité sur le mode de signalisation).

