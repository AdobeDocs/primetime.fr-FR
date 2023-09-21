---
title: TVSDK 1.4 à 2.5 pour Android (Java)
description: TVSDK 2.5 offre plusieurs avantages par rapport à la version 1.4 en termes de performances, de sécurité, d’meilleures intégrations, etc.
contentOwner: vishgupt
products: SG_PRIMETIME
topic-tags: migration
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 0%

---

# TVSDK 1.4 à 2.5 pour Android (Java) {#tvsdk-to-for-android-java}

TVSDK 2.5 offre plusieurs avantages par rapport à la version 1.4 en termes de performances, de sécurité, d’meilleures intégrations, etc.

TVSDK résout les plus grands défis, sur l’appareil qui compte le plus. Android continue sa domination mondiale, avec plus de 86% des parts de marché. La migration vers TVSDK sur Android optimise les performances de lecture afin d’améliorer l’engagement des utilisateurs et d’accélérer le délai de mise sur le marché avec la prise en charge de nouveaux formats de contenu.

## Avantages de la migration vers TVSDK v2.5 {#benefits-of-migrating-to-tvsdk-v}

TVSDK 2.5 offre plusieurs avantages par rapport à la version 1.4 en termes de performances, de sécurité, d’meilleures intégrations, etc. Lisez la suite pour connaître rapidement les avantages de la migration vers cette nouvelle version.

Selon une étude tierce d’évaluation des performances, la version 2.5 offre une réduction de 5 fois le temps de démarrage et de 3,8 fois le nombre d’images perdues par rapport à la moyenne du secteur.

| Fonctionnalités de performances | Description |
|--- |--- |
| Instant pour VOD et Live | Précharger les segments initiaux pour la lecture immédiate pour les flux VOD et linéaires en direct lors du changement de canal, pour une expérience de type TV. |
| Chargement différé des publicités | Commence la lecture dès que le contenu ou le preroll est disponible lors de la résolution des publicités mid-roll dans un thread parallèle. |
| Connexions réseau persistantes | Amélioration de l’efficacité et diminution de la latence du code réseau pour accélérer les performances de lecture. |
| Amélioration de la logique ABR | La nouvelle logique ABR repose sur la longueur de la mémoire tampon, le taux de changement de la longueur de la mémoire tampon et la bande passante mesurée. Ainsi, l’ABR choisit le débit approprié lorsque la bande passante fluctue et optimise le nombre de fois où le changement de débit se produit réellement en surveillant la vitesse à laquelle la longueur de la mémoire tampon change. |
| Téléchargement partiel de segments | Commence la lecture dès que suffisamment d’images d’un segment sont disponibles pour un rendu vidéo fiable côté client. |
| Téléchargements parallèles | TVSDK télécharge les segments audio et vidéo en parallèle pour le contenu décompressé afin d’optimiser les performances de lecture. |

Les fonctionnalités de lecture améliorent l’engagement des consommateurs en fournissant l’expérience de la diffusion linéaire sur le numérique. Cela vous permet également d’exploiter le DRM natif tel que Widevine pour la lecture HD.

| Fonctionnalités de lecture | Description |
|--- |--- |
| Lecture MP4 | Il n’est pas nécessaire de retranscoder les extraits MP4 courts en lecture dans TVSDK. |
| Lecture du contenu VOD DASH | Les cas d’utilisation de lecture de base DASH VOD sont pris en charge. |
| Lissage du trickplay avec ABR | Prise en charge de l’avance rapide et du rembobinage en HLS à l’aide d’images clés à faible débit et d’images I à vitesse supérieure. Prise en charge de la technologie ABR pour toutes les images prises en charge. |

Les fonctionnalités sont importantes pour répondre aux restrictions du studio telles que la lecture HD sur DRM natif.

| Fonctionnalités | Description |
|--- |--- |
| Protection des sorties basée sur la résolution | La lecture peut être limitée à certaines résolutions autorisées par les exigences DRM. Disponible uniquement via Primetime DRM. |
| Prise en charge des appareils sans fil | Pris en charge avec les flux VOD DASH pour activer les cas d’utilisation DRM natifs. |

L’amélioration de la facturation directe élimine la nécessité de créer des rapports manuels pour la facturation tous les mois. VHL 2.0 permet de commercialiser plus rapidement l’intégration précompilée et une meilleure précision du suivi.

| Fonctionnalités | Description |
|--- |--- |
| Intégration de la souris | Prise en charge de la mesure de la visibilité publicitaire de la souris. |
| VHL 2.0 | La dernière intégration optimisée de la bibliothèque de pulsations vidéo pour la collecte automatique des données d’utilisation d’Adobe Analytics. |
| Prise en charge du basculement | Des stratégies supplémentaires ont été mises en oeuvre pour poursuivre la lecture ininterrompue, en dépit des échecs des serveurs d’hôtes, des fichiers de liste de lecture et des segments. |
| Intégration de la facturation directe | Envoie les mesures de facturation au serveur principal Adobe Analytics, qui est certifié par Adobe Primetime pour les diffusions utilisées par le client. |

>[!NOTE]
>
>Toutes les fonctionnalités de TVSDK v1.4 sont prises en charge dans v2.5, à l’exception de la prise en charge de plusieurs CDN.

## Présentation du processus de migration {#overview-of-the-migration-process}

La migration en douceur de TVSDK 1.4 vers 2.5 implique de passer aux bibliothèques de la version 2.5, de recompiler, puis d’utiliser ce document pour aider à déboguer les problèmes qui se produisent.

Les bibliothèques TVSDK v1.4 ne fonctionnent pas avec les bibliothèques v2.5 et ne coexistent pas avec elles. Vous devez utiliser les bibliothèques v2.5 avec TVSDK 2.5 et migrer vos applications et intégrations vers TVSDK 2.5. Ce document décrit comment et quoi modifier le code de votre application et comment corriger les erreurs lors de la recompilation.

Le fichier psdk.jar utilise des bibliothèques tierces pour prendre en charge différentes fonctionnalités. Pour empêcher la suppression des bibliothèques, incluez les éléments suivants dans la variable `proguard.cfg` fichier :

```java
# Adobe TVSDK keep classes
-keep class com.adobe.** { *; }
-keep class com.google.android.exoplayer.**
{ *; }
```

Dans le `build.gradle` , vous devez inclure la directive de compilation pour inclure les fichiers JAR basés sur TVSDK. Si votre application inclut Adobe Video Analytics, vous devez inclure la directive de compilation pour les fichiers JAR supplémentaires requis pour l’intégration de Adobe Video Analytics dans l’application.

```java
# Compile Adobe TVSDK jars compile files('libs/psdk-va.jar')
compile files('libs/VideoHeartbeat.jar')
```

Plusieurs modifications mineures ne sont pas abordées dans ce document. Pour connaître les modifications mineures apportées à l’API, reportez-vous à la section [TVSDK 2.5 pour API Java Android](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.5/index.html). La référence d’API C++ correspondante contient des descriptions détaillées. Pour consulter la documentation de l’API C++ analogue, voir [API TVSDK 2.5 pour Android C++](https://help.adobe.com/en_US/primetime/api/psdk/cpp_2.5/index.html).

Plusieurs exemples d’utilisation de l’API sont abordés dans la mise en oeuvre de référence distribuée avec TVSDK.

## Modifications des API dans TVSDK v2.5 {#api-changes-in-tvsdk-v}

Les nouvelles API, obsolètes et modifiées sont décrites ci-dessous.

| TVSDK v1.4 | TVSDK v2.5 | Description |
|--- |--- |--- |
| import com.adobe.ave.drm.DRMAcquireLicenseSettings | import com.adobe.mediacore.drm.DRMAcquireLicenseSettings; | Tous les noms de classe dans l’API TVSDK 2.5 commencent par le préfixe com.adobe.mediacore . Ce n&#39;est qu&#39;un exemple. |
| MediaPlayerException, IllegalStateException ou IllegalArgumentException | MediaPlayerException | Dans la version 2.5, les API génèrent uniquement MediaPlayerException. |
| MediaPlayer.PlayerState (MediaPlayer.Event.PLAYBACK) | MediaPlayerStatus (MediaPlayerEvent.STATUS_CHANGED) | Dans la version 2.5, MediaPlayer.PlayerState a été renommé MediaPlayerStatus dans une énumération distincte. |
| DefaultMediaPlayer.create (getActivity().getApplicationContext()) | MediaPlayer mediaPlayer = new MediaPlayer(getActivity(). getApplicationContext()); | Les méthodes statiques utilisées pour créer des objets sont remplacées par des constructeurs publics. |
| MediaPlayer.seekToLocalTime() | MediaPlayer.seekToLocal() | La méthode MediaPlayer.searchToLocalTime() est désormais appelée MediaPlayer.searchToLocal(). |
| closedCaptionsTrack.isActive() |  | Non disponible |
| MetadataNode | Métadonnées | Dans la version 2.5, la classe Metadata remplace l’utilisation de la classe MetadataNode de la version 1.4. |
| DefaultMetadataKeys | MetadataKeys | Les DefaultMetadataKeys de la version 1.4 sont dans la version 2.5 de MetadataKeys. |
| AdvertisingFactory | ContentFactory | AdvertisingFactory de la version 1.4 est renommée ContentFactory dans la version 2.5. |
| PlacementOpportunityDetector | OpportunityGenerator | Les détecteurs sont remplacés par des générateurs. |
| mediaPlayer.getView().notifyClick(); | mediaPlayer.notifyClick(); | La méthode notifyClick() de MediaPlayerView a été déplacée vers la classe MediaPlayer . |
| public ABRControlParameters(ABRPolicy abrPolicy, int nInitialBitRate, int nMinBitRate, int nMaxBitRate) | public ABRControlParameters(int nInitialBitRate, int nMinBitRate, int nMaxBitRate, ABRPolicy abrPolicy, int MinTrickPlayBitRate, int nMaxTrickPlayBitRate, int nMaxTrickPlayBandwidthUsage, double d MaxPlayoutRate) |  |
| playbackInformation.getTimeToFirstFrame() |  | Non disponible |
|  | playbackInformation.get PerceivedBandwidth() | TVSDK v2.5 QOSProvider possède une nouvelle propriété pour déterminer la bande passante perçue lors d’une session de diffusion en continu. |

### Classes supprimées {#removed-classes}

Les classes suivantes sont supprimées et n’ont aucun équivalent.

* `TimeRangeCollection`
* `PSDKConfig`
* `BaseLogger`
* `DefaultLogger`
* `Log`
* `Logger`
* `LogFactory`
* `NullLogger`

Les six dernières de ces classes sont disponibles en tant que classes d’utilitaires dans l’implémentation de référence.

## Modifications des espaces de noms {#namespace-changes}

L’API TVSDK 2.5 regroupe les espaces de noms.

Tous les noms de classe dans l’API TVSDK 2.5 commencent par le préfixe com.adobe.mediacore . Certains noms de classe dans l’API TVSDK 1.4 commencent par com.adobe.ave. Les classes 2.5 correspondantes changent com.adobe.ave en com.adobe.mediacore. Par exemple, notez les modifications apportées aux lignes de code 1.4 et 2.5 suivantes :

```java
// TVSDK 1.4
import com.adobe.ave.drm.DRMAcquireLicenseSettings; import com.adobe.ave.drm.DRMLicense;
import com.adobe.ave.drm.DRMManager; import com.adobe.ave.drm.DRMMetadata
```

```java
// TVSDK 2.5
import com.adobe.mediacore.drm.DRMAcquireLicenseSettings; import com.adobe.mediacore.drm.DRMLicense;
import com.adobe.mediacore.drm.DRMManager; import com.adobe.mediacore.drm.DRMMetadata;
```

## Modifications de la gestion des événements {#changes-in-event-handling}

Pour enregistrer des événements dans cette version, transmettez le gestionnaire à `addEventListener`. La liste des événements a été considérablement revue de la version 1.4 à la version 2.5.\
Par exemple, voici comment enregistrer un gestionnaire d’événements pour `MediaPlayerEvent.STATUS_CHANGED:`

```java
mPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,
new StatusChangeEventListener() {
@Override
public void onStatusChanged(MediaPlayerStatusChangeEvent event) {
//Handle status change event
}
});
```

Voici comment l’événement a été enregistré dans la version 1.4 :

```java
mPlayer.addEventListener(MediaPlayer.Event.PLAYBACK, new MediaPlayer.PlaybackEventListener() {
@Override
public void onStateChanged(MediaPlayer.PlayerState state,
MediaPlayerNotification notification) {
//Handle status change event
}
// Additional handlers
...
});
```

L’énumération MediaPlayerEvent contient tous les codes d’événement. Les codes d’événement suivants de la version 1.4 n’existent plus dans la version 2.5 :

* `ADBREAK_PLACEMENT_COMPLETED`
* `ADBREAK_PLACEMENT_FAILED`
* `ADBREAK_REMOVAL_COMPLETED`
* `AD_BREAK_MANIFEST_LOAD_COMPLETE`
* `AD_MANIFEST_LOAD_COMPLETE`
* `AD_MANIFEST_LOAD_FAILED`
* `AUDIO_TRACK_FAILED`
* `BACKGROUND_MANIFEST_FAILED`
* `BUFFERING_FULL, CUSTOM_AD_EVENT`
* `CONTENT_MARKER`
* `CONTENT_PLACEMENT_COMPLETE`
* `CONTENT_CHANGED`
* `ITEM_REPLACED`
* `ITEM_READY`
* `VIEW_CLICKED`
* `PREPARED`
* `UPDATED`
* `OPPORTUNITY_COMPLETED`
* `OPPORTUNITY_CREATED`
* `OPPORTUNITY_FAILED`
* `PAUSE_AT_PERIOD_END`
* `PLAYBACK_STARTED`
* `PLAYBACK_PAUSED`
* `PLAYBACK_COMPLETED`
* `PLAY_COMPLETE`
* `POST_ROLL_COMPLETE`
* `RESOURCE_LOADED`
* `TIMED_METADATA_SKIPPED`
* `VIDEO_ERROR`
* `VIDEO_STATE_CHANGED`

Les codes d’événement suivants sont nouveaux dans la version 2.5 :

* `AD_RESOLUTION_COMPLETE`
* `BUFFER_PREPARED`
* `CAPTIONS_UPDATED`
* `MANIFEST_UPDATED`
* `PLAYBACK_RANGE_UPDATED`
* `RESERVATION_REACHED`
* `TIME_CHANGED`
* `TIMED_EVENT`
* `TIMED_METADATA_ADDED_IN_BACKGROUND`

### Événements renommés {#renamed-events}

| Nouveau nom | Ancien nom |
|--- |--- |
| SEEK_BEGIN | SEEK_STARTED |
| SEEK_END | SEEK_COMPLETED |
| SEEK_POSITION_ADJUSTED | SEEK_ADJUST_COMPLETED |
| BUFFERING_BEGIN | BUFFERING_STARTED |
| BUFFERING_END | BUFFERING_COMPLETED |
| AUDIO_TRACK_UPDATED | AUDIO_TRACK_CHANGED |
| STATUS_CHANGED | STATE_CHANGED |
| TIMED_METADATA_AVAILABLE | TIMED_METADATA_ADDED |
| SIZE_AVAILABLE | SIZE_CHANGED |
| LOAD_INFO | LOAD_INFORMATION_AVAILABLE |

## Modifications du lecteur multimédia {#mediaplayer-changes}

Une nouvelle manière de construire `MediaPlayer` et modifications apportées à certaines méthodes.

**Modifications apportées à la classe MediaPlayer**

Voici les modifications apportées à `MediaPlayer` Classe :

* La variable `MediaPlayerStatus` enum remplace `MediaPlayer.PlayerState`. Par exemple :

```java
//TVSDK v1.4
mPlayer. addEventListener(MediaPlayer.Event.PLAYBACK, new MediaPlayer.PlaybackEventListener() {

@Override
public void onStateChanged(MediaPlayer.PlayerState state,MediaPlayerNotification notification) {
//Handle status change event
}
// Additional handlers
...
});

//TVSDK v2.5
mPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED, new StatusChangeEventListener() {
@Override
public void onStatusChanged(MediaPlayerStatusChangeEvent event) {
//Handle status change event
}
//Additional handlers.
...
});
```

* La variable `MediaPlayer.seekToLocalTime()` est désormais appelée `MediaPlayer.seekToLocal`. Par exemple :

```java
//TVSDK v1.4
public void seekToLocal(long localPosition) { mediaPlayer.seekToLocalTime(localPosition);
}

//TVSDK v2.5
public void seekToLocal(long localPosition) { mediaPlayer.seekToLocal(localPosition);
}
```

* La variable `MediaPlayerView.notifyClick()` est maintenant `MediaPlayer.notifyClick()`. Par exemple :

```java
//TVSDK v1.4
public void adClick() { mediaPlayer.getView().notifyClick();
}

//TVSDK v2.5
public void adClick() { mediaPlayer.notifyClick();
}
```

* Le premier `MediaPlayer.MediaPlayer.getNotificationHistory()` a disparu et n’a pas été remplacée.
* Le premier `MediaPlayer.replaceCurrentItem()` est divisé en deux méthodes : `replaceCurrentResource()`, qui utilise une instance de `MediaResource`, et `replaceCurrentItem()`, qui utilise une instance de `MediaPlayerItem`. Par exemple :

```java
//TVSDK v1.4
MediaResource playerResource = MediaResource.createFromUrl(url, getAdvertisingMetadata());

mediaPlayer.replaceCurrentItem(playerResource);

//TVSDK v2.5 - replacing a resource
MediaResource playerResource = new MediaResource(url,
MediaResource.Type.HLS, getAdvertisingMetadata());
...
try {
mMediaPlayer.replaceCurrentResource(playerResource, _mediaPlayerItemConfig);
} catch (MediaPlayerException mediaPlayerException) {
// handle exception.
}
// TVSDK 2.5 - replacing an Item
MediaPlayerItemLoader itemLoader = new MediaPlayerItemLoader(context, new MediaPlayerItemLoader.LoaderListener() {

@Override
public void onError(PSDKErrorCode psdkErrorCode, String s) {
...
}
@Override
public void onLoadComplete(MediaPlayerItem mediaPlayerItem) {
...
}
@Override
public void onBufferingBegin() {
...
}
@Override
public void onBufferPrepared() {
...
}
});
MediaResource playerResource = new MediaResource(url,
MediaResource.Type.HLS, getAdvertisingMetadata());

itemLoader.load(playerResource); itemLoader.prepareBuffer();
mediaPlayer.replaceCurrentItem(itemLoader.getItem());
```

Vous pouvez l’utiliser pour basculer entre les instances MediaPlayer préinitialisées, comme dans le cas de pannes de courant.

**Les constructeurs remplacent les méthodes create() statiques**

Vous pouvez utiliser des constructeurs dans TVSDK v2.5 au lieu d’utiliser `create()` méthodes de TVSDK v1.4. Toutes les classes dont les noms commencent par défaut, telles que `DefaultMediaPlayer`, `DefaultNetworkConfig`, `DefaultContentFactory`, ne sont pas disponibles dans v2.5.

Dans certains cas, l’API TVSDK v1.4 utilise le modèle suivant pour créer des classes :

1. Définir une interface (par exemple, `MediaPlayer`).
1. Fournissez une classe par défaut (par exemple, `DefaultMediaPlayer`).
1. Fournissez une `create()` sur la classe par défaut pour fournir une classe qui implémente l’interface.

Dans TVSDK v2.5, ces interfaces sont des classes concrètes et vous créez des instances de ces classes à l’aide des constructeurs respectifs. Les fragments de code suivants illustrent cette différence :

```java
//TVSDK v1.4
// Create a media player
// MediaPlayer is an interface
private MediaPlayer createMediaPlayer() { MediaPlayer mediaPlayer =
DefaultMediaPlayer.create(getActivity().getApplicationContext()); return mediaPlayer;

//TVSDK v2.5
// Create a media player
// MediaPlayer is a class that you instantiate private MediaPlayer createMediaPlayer() {
MediaPlayer mediaPlayer =
new MediaPlayer(getActivity().getApplicationContext()); return mediaPlayer;
}
```

D’autres classes qui ne suivent pas ce modèle mais utilisent `create()` dans la version 1.4, les méthodes suivantes sont disponibles :

* MediaResource\
  Anciennement utilisée `MediaResource.createFromUrl()`. Maintenant, utilisez le constructeur qui prend une URL, un type de ressource et des métadonnées. Par exemple :

```java
//TVSDK v1.4
MediaResource playerResource = MediaResource.createFromUrl(url, getAdvertisingMetadata());
mediaPlayer.replaceCurrentItem(playerResource);

//TVSDK v2.5
MediaResource playerResource =
new MediaResource(url, MediaResource.Type.HLS, getAdvertisingMetadata());

try { mediaPlayer.replaceCurrentResource(playerResource,_mediaPlayerItemConfig);
} catch (MediaPlayerException mediaPlayerException) {
// handle exception.
}
```

* Publicité
* AdAsset
* AdBreak

Certaines classes (par exemple, `ContentFactory`) sont des classes abstraites sans mise en oeuvre par défaut disponible publiquement (par exemple, `DefaultContentFactory`). Dans ce cas, vous pouvez fournir une implémentation par défaut via une fonction pratique, par exemple : `mediaPlayerItemConfig.getDefaultContentFactory()`

**Modifications du sous-titrage codé**

Les modifications suivantes affectent les classes liées au sous-titrage :

* Lors de la récupération du suivi des sous-titres, `MediaPlayerItem.getClosedCaptionTracks()` renvoie uniquement les suivi actifs.
* `ClosedCaptionTrack` n’a plus de `isActive()` .

```java
//TVSDK v1.4
public List<String> getClosedCaptionTracks(String label) {
List<String> closedCaptionsTracksAsStrings = new ArrayList<String>(); MediaPlayerItem currentItem = mediaPlayer.getCurrentItem(); List<ClosedCaptionsTrack> closedCaptionsTracks =
currentItem.getClosedCaptionsTracks(); Iterator<ClosedCaptionsTrack> iterator =
closedCaptionsTracks.iterator();
if (currentItem != null) {
while (iterator.hasNext()) {
ClosedCaptionsTrack closedCaptionsTrack = iterator.next(); String isActive = closedCaptionsTrack.isActive() ? " (" + label
+ ")" : "";
closedCaptionsTracksAsStrings.add(closedCaptionsTrack.getName()
+ " : " + closedCaptionsTrack.getLanguage() + isActive);
}
}
return closedCaptionsTracksAsStrings;
}

//TVSDK v2.5
public List<String> getClosedCaptionTracks(String label) {

MediaPlayerItem currentItem = mediaPlayer.getCurrentItem(); List<ClosedCaptionsTrack> closedCaptionsTracks =
currentItem.getClosedCaptionsTracks();
Iterator<ClosedCaptionsTrack> iterator = closedCaptionsTracks.iterator();

List<String> closedCaptionsTracksAsStrings = new ArrayList<String>(); if (currentItem != null) {
while (iterator.hasNext()) {
ClosedCaptionsTrack closedCaptionsTrack = iterator.next(); closedCaptionsTracksAsStrings.
add(closedCaptionsTrack.getName() + " : ");
}
}
return closedCaptionsTracksAsStrings;
}
// Add snippet and desc for CaptionsUpdatedEventListener mediaPlayer.addEventListener(MediaPlayerEvent.CAPTIONS_UPDATED,
captionsUpdatedEventListener);

private final CaptionsUpdatedEventListener captionsUpdatedEventListener = new CaptionsUpdatedEventListener() {

@Override
public void onCaptionsUpdated(MediaPlayerItemEvent mediaPlayerItemEvent) { getActivity().findViewById(R.id.sbPlayerControlCC).setVisibility(
View.VISIBLE/*Visible*/);
}
};
```

## Modifications publicitaires {#advertising-changes}

Il existe plusieurs modifications liées aux publicités dans la version 2.5.

**Modifications du comportement publicitaire**

Le comportement par défaut de la lecture de la publicité lorsqu’un utilisateur effectue une recherche au-delà d’une capsule publicitaire change légèrement dans la version 2.5. Si la coupure publicitaire n’est pas visionnée, la publicité est lue après une recherche vers l’avant. Lorsque l’application utilise la stratégie de publicité par défaut, la coupure publicitaire est supprimée une fois la lecture terminée. Si, à l’aide de TVSDK v2.5, un utilisateur effectue une recherche derrière une capsule publicitaire dans la chronologie et que la coupure publicitaire n’est pas visionnée, aucune publicité n’est lue.

Cependant, dans TVSDK v1.4, par défaut, une publicité est lue en cas de recherche en amont. Par exemple, si vous effectuez une recherche en amont entre la troisième et la quatrième coupure publicitaire, le comportement par défaut de TVSDK v1.4 consiste à lire la troisième coupure publicitaire.

**Modification des règles publicitaires**

Les règles publicitaires sont spécifiées à l’aide d’un fichier JSON. Le format du fichier JSON reste le même dans les deux versions de TVSDK. Toutefois, dans TVSDK v2.5, le fichier JSON des règles publicitaires doit être hébergé sur un emplacement accessible via une URL HTTP. L’application peut utiliser une instance de AuditudeSettings.

```java
//TVSDK v2.5
AuditudeSettings result = new AuditudeSettings(); result.setCRSRulesJsonURL(<http url of AdobeTVSDKConfig.json>);
```

Dans TVSDK version 1.4, ce fichier est placé sous le dossier assets de l’application et TVSDK charge le fichier.

**Changement de nom d’usine des publicités**

`AdvertisingFactory` est désormais nommé `ContentFactory`. Avec `ContentFactory` vous pouvez créer des workflows publicitaires personnalisés en remplaçant certaines de ses méthodes. Utilisez return null pour conserver les comportements par défaut, comme dans l’exemple suivant :

```java
//TVSDK v2.5
new ContentFactory() {
@Override
public AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem item) { return new CustomAdPolicySelector();
}
@Override
public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { return null;
}
@Override
public List<ContentResolver> retrieveResolvers(MediaPlayerItem item) { return null;
}
@Override
public List<CustomAdHandler> retrieveCustomAdPlaybackHandlers(MediaPlayerItem item) { return null;
}
};
```

**Sauts publicitaires de durée nulle**

TVSDK 2.5 insère des coupures publicitaires de longueur nulle en tant qu’espaces réservés lorsque le serveur de publicité ne renvoie aucune publicité.

Vous pouvez déterminer la longueur zéro des coupures publicitaires en détectant le nombre de publicités à zéro dans la coupure publicitaire à l’aide de l’événement onAdBreakStarted et l’application doit gérer ces coupures publicitaires en conséquence.

**Modifications des métadonnées**

La classe Metadata remplace plus efficacement l’ancienne classe MetadataNode.

* La classe Metadata peut stocker des chaînes, des tableaux d’octets et d’autres objets Metadata :

```java
TVSDK v1.4
public AuditudeSettings createAdvertisementSettings() { Metadata advertisingParams = new MetadataNode();
advertisingParams.setValue("platform", Build.VERSION.RELEASE); advertisingParams.setValue("model", Build.MODEL);
AuditudeSettings adSettings = new AuditudeSettings();
// Set ad domain, zone id and media_id
...

// Set the target paramaters adSettings.setTargetingParameters(advertisingParams);

return adSettings;
}
//TVSDK v2.5
public AuditudeSettings createAdvertisementSettings() { Metadata advertisingParams = new Metadata();
advertisingParams.setValue("platform", Build.VERSION.RELEASE); advertisingParams.setValue("model", Build.MODEL);
AuditudeSettings adSettings = new AuditudeSettings();
// Set ad domain, zone id and media_id
...

// Set the target paramaters adSettings.setTargetingInfo(advertisingParams);

return adSettings;
}
```

* La variable `MetadataKeys` enum remplace `DefaultMetadataKeys`. Toutes les clés de `DefaultMetadataKeys` sont présents dans la nouvelle version.

```java
//TVSDK v1.4
if (this.mediaPlayer != null && this.mediaPlayer.getCurrentItem() != null) { MetadataNode resourceMetadata =
(MetadataNode) this.mediaPlayer.getCurrentItem().getResource().getMetadata();
VideoAnalyticsMetadata vaMetadata = (VideoAnalyticsMetadata)
resourceMetadata.getNode(DefaultMetadataKeys.
VIDEO_ANALYTICS_METADATA_KEY.getValue());
}

//TVSDK v2.5
if (resourceMetadata.containsKey(VideoAnalyticsMetadata.
VIDEO_ANALYTICS_METADATA_KEY)) {
JSONObject vaMetadataObj =
new JSONObject(resourceMetadata.
getValue(VideoAnalyticsMetadata. VIDEO_ANALYTICS_METADATA_KEY));
vaMetadata = parseVideoAnalyticsMetadata(vaMetadataObj);
}

} catch (JSONException e) { e.printStackTrace();
}
```

* Les métadonnées publicitaires sont désormais représentées par le `AdvertisingMetadata` , sous-classe de métadonnées et est désormais stockée dans `MediaPlayerItemConfig` plutôt que `MediaResource`.

```java
//TVSDK v1.4
MetadataNode mediaMetadata = new MetadataNode();

if (stream.live) { mediaMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY.getValue(),
getAdSettingsForLive());
} else {
mediaMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY.getValue(), getAdSettingsForVod());
}
MediaResource playerResource = MediaResource.createFromUrl(url, mediaMetadata);

//TVSDK v2.5
MediaPlayerItemConfig mediaItemConfig = new MediaPlayerItemConfig(context);

if (stream.live) {
AuditudeSettings adSettings = getAdSettingsForLive(); adSettings.setLivePreroll(true); mediaItemConfig.setAdvertisingMetadata(adSettings);
} else {
// Set the advertising parameters for VOD. mediaItemConfig.setAdvertisingMetadata(getAuditudeSettingsForVod());
}

// Create advertising metadata node Metadata mediaMetadata = new Metadata();

// Asset Url
MediaResource playerResource =
new MediaResource(url, MediaResource.Type.HLS, mediaMetadata);
try {
mediaPlayer.replaceCurrentResource(playerResource, mItemConfig);
} catch (MediaPlayerException mediaPlayerException) {
//handle exception.
}
```

Métadonnées de configuration réseau, anciennement membres de la fonction `MediaResource` , est désormais représentée par la fonction `NetworkConfiguration` et est désormais stockée dans `MediaPlayerItemConfig` plutôt que `MediaResource`.

```java
//TVSDK v1.4
MediaResource playerResource = MediaResource.createFromUrl(url, mediaMetadata);
...

//TVSDK v2.5
MediaPlayerItemConfig mediaItemConfig = new MediaPlayerItemConfig(context);

NetworkConfiguration mediaNetworkConfiguration = mediaItemConfig.getNetworkConfiguration();
```

**Modifications apportées à l’analyse des métadonnées temporelles**

L&#39;analyse de `TimedMetadata` a été modifié dans la version 2.5 en ce qui concerne les types de données pour l’analyse de la balise ID3.

```java
//TVSDK v1.4
public void onTimedMetadata(TimedMetadata timedMetadata) { TimedMetadata.Type type = timedMetadata.getType();
if (type.equals(TimedMetadata.Type.ID3)){ PMPDemoApp.logger.i(LOG_TAG + "#onTimedMetadata",
"New ID3 tag detected at time = " + timedMetadata.getTime());
Metadata metadata = timedMetadata.getMetadata(); Set<String> keys = metadata.keySet();
for (String key : keys) {
String value = metadata.getValue(key); PMPDemoApp.logger.i(LOG_TAG + "#onTimedMetadata",
"Key = " + key + " Value = " + value);
}
} else if (_mediaPlayer.getPlaybackRange() != null &&
_mediaPlayer.getPlaybackRange().getDuration() > 0) { displayRanges();
PMPDemoApp.logger.i(LOG_TAG +
"#onTimedMetadata",
"New timed metadata. Name " + timedMetadata.getName() +
", time " + timedMetadata.getTime() + ", id " + timedMetadata.getId() + ", metadata " +
timedMetadata.getMetadata() + ".");
/*if (!_timedMetadataList.contains(timedMetadata)) {
_timedMetadataList.add(timedMetadata);
}*/
/* scte35 */
if (timedMetadata.getName().equalsIgnoreCase("#EXT-OATCLS-SCTE35")) { parseSCTE35Tag(timedMetadata);
}
}
}

//TVSDK v2.5
public void onTimedMetadata(TimedMetadataEvent timedMetadataEvent) { PMPDemoApp.logger.i(LOG_TAG + " inside"," ontimedmetadata"); TimedMetadata timedMetadata = timedMetadataEvent.getTimedMetadata();

TimedMetadata.Type type = timedMetadata.getType(); if (type.equals(TimedMetadata.Type.ID3)) {
PMPDemoApp.logger.i(LOG_TAG +
"#onTimedMetadata",
"New ID3 tag detected at time = " + timedMetadata.getTime());
Metadata metadata = timedMetadata.getMetadata();
if (metadata != null) { PMPDemoApp.logger.i(LOG_TAG +
"::expandID3Metadata", "isEmpty " + metadata.isEmpty());
Set<String> keys = metadata.keySet(); PMPDemoApp.logger.i(LOG_TAG + "::expandID3Metadata",
"No of keys=" + keys.size());
String s;
for (String key : keys) {
byte[] value = metadata.getByteArray(key); s = new String(value);
if (key.equalsIgnoreCase("APIC"))
s = "SUPPRESSING BINARY DATA FOR ATTACHED PICTURE.";
PMPDemoApp.logger.i(LOG_TAG + "::expandID3Metadata",
"Key=" + key + ", Length=" + value.length + ", Value=" + s.trim());
}
}
} else if (_mediaPlayer.getPlaybackRange() != null &&
_mediaPlayer.getPlaybackRange().getDuration() > 0) { displayRanges();
PMPDemoApp.logger.i(LOG_TAG +
"#onTimedMetadata",
"New timed metadata. Name " + timedMetadata.getName() +
", time " + timedMetadata.getTime() + ", id " + timedMetadata.getId() + ", metadata " +
timedMetadata.getMetadata() + ".");
/*if (!_timedMetadataList.contains(timedMetadata)) {
_timedMetadataList.add(timedMetadata);
}*/
/* scte35 */
if (timedMetadata.getName().equalsIgnoreCase("#EXT-OATCLS-SCTE35")) { PMPDemoApp.logger.i(LOG_TAG +
" inside ontimedmetadata"," ext"); parseSCTE35Tag(timedMetadata);
}
}
}
```

**Autres modifications**

Les modifications supplémentaires suivantes sont disponibles dans la version 2.5 :

* La variable `notifyClick()` a été déplacée de `MediaPlayerView` to `MediaPlayer`.

* `AdPolicySelector` est une interface, et non une classe. Mettez en oeuvre toutes ses méthodes.
* `AdPolicyInfo` contient désormais une liste de `AdBreakTimelineItem`, not `AdBreakPlacement`.

* Nom de l’API de `ContentResolver` la classe abstraite a été modifiée.
* `PlacementOpportunityDetector` n’est plus disponible. Au lieu de cela, étendez la variable `OpportunityGenerator` classe abstraite. L’implémentation de référence en fournit un exemple.

* Les paramètres de la variable `AdBreakPlacement` Le constructeur est le même, mais dans un ordre différent. Pour obtenir un exemple de mise en oeuvre, reportez-vous à la section Mise en oeuvre du lecteur de référence fournie avec le produit .

## Changements dans DRM {#changes-in-drm}

La plupart des modifications apportées à cette version se trouvent dans la couche DRM. Le tableau suivant présente des modifications supplémentaires entre les versions 1.4 et 2.5 :

| Méthode DRMManager | Rappel de succès dans 1.4 | Rappel d’erreur dans 1.4 | Écouteur dans 2.5 |
|--- |--- |--- |--- |
| acquireLicense | DRMLicenseAcquiredCallback | DRMOperationErrorCallback | DRMAcquireLicenseListener |
| acquirePreviewLicense | DRMLicenseAcquiredCallback | DRMOperationErrorCallback | DRMAcquireLicenseListener |
| authentifier | DRMAuthenticationCompleteCallback | DRMOperationErrorCallback | DRMAuthenticateListener |
| createMetadataFromBytes | NA | DRMOperationErrorCallback | DRMErrorListener |
| initialize | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| joinLicenseDomain | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| leaveLicenseDomain | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| resetDRM | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| returnLicense | DRMLicenseReturnCompleteCallback | DRMOperationErrorCallback | DRMReturnLicenseListener |
| setAuthenticationToken | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| storeLicenseBytes | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |

```java
//TVSDK 1.4
private final MediaPlayer.DRMEventListener _drmEventListener = new MediaPlayer.DRMEventListener() {

@Override
public void onDRMMetadata(final DRMMetadataInfo drmMetadataInfo) { PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.DRMEventListener#onDRMMetadata",
"DRM metadata available: " + drmMetadataInfo + ".");
if (getSuppressAutoPlayPreference() && drmMetadataInfo != null) {
// if suppress play setting, then the user is a tester who
// wishes to manually intervene between the metadata available
// event and the play event, so launch the metadata interface
// and give it the loaded metadata bytes, but only once
_drmMetadata = drmMetadataInfo.getDRMMetadata();
}
if (drmMetadataInfo == null ||
!DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { PMPDemoApp.logger.i(LOG_TAG + "#onDRMMetadata", "DRM auth is not needed."); return;
}
// Perform DRM auth.
// Possible logic might take into consideration a threshold
// between the current player time and the DRM metadata start
// time. For the time being, we resolve it as soon as we receive
// the DRM metadata.

DRMManager drmManager = _mediaPlayer.getDRMManager(); if (drmManager == null) {
PMPDemoApp.logger.e(LOG_TAG + "#onDRMMetadata", "DRMManager is null."); return;
}
SharedPreferences sharedPreferences =
PreferenceManager.getDefaultSharedPreferences(getActivity()); String authUser =
sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_USERNAME,
getResources().getString(R.string.drmUsername));
String authPass = sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_PASSWORD,
getResources().getString(R.string.drmPassword));
DRMHelper.performDrmAuthentication(drmManager,
drmMetadataInfo.getDRMMetadata(), authUser,
authPass,
new DRMAuthenticationListener() {
@Override
public void onAuthenticationStart() { PMPDemoApp.logger.i(LOG_TAG + "#onAuthenticationStart",
"DRM authentication started for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
@Override
public void onAuthenticationError(long majorCode,
long minorCode, Exception e) {
if (getActivity() == null) { return;
}
PMPDemoApp.logger.e(LOG_TAG +
"#onAuthenticationError",
"DRM authentication failed. " + majorCode + " 0x" + Long.toHexString(minorCode));
_handler.post(new Runnable() {
@Override
public void run() { showToast(getString(R.string.drmAuthenticationError)); getActivity().finish();
}
});
}
@Override
public void onAuthenticationComplete(byte[] authenticationToken) { PMPDemoApp.logger.i(LOG_TAG +
"#onAuthenticationComplete",
"Auth successful for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
});
}
};

//TVSDK 2.5
private final DRMMetadataInfoEventListener drmMetadataInfoEventListener = new DRMMetadataInfoEventListener() {
@Override
public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { final DRMMetadataInfo drmMetadataInfo =
drmMetadataInfoEvent.getDRMMetadataInfo();
PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.DRMEventListener#onDRMMetadata",
"DRM metadata available: " + drmMetadataInfo + ".");
if (getSuppressAutoPlayPreference() && drmMetadataInfo != null) {
// if suppress play setting, then the user is a tester who
// wishes to manually intervene between the metadata
// available event and the play event, so launch the
// metadata interface and give it the loaded metadata
// bytes, but only once
drmMetadata = drmMetadataInfo.getDRMMetadata();
}
if (drmMetadataInfo ==
null || !DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { PMPDemoApp.logger.i(LOG_TAG +
"#onDRMMetadata",
"DRM auth is not needed.");
return;
}
// Perform DRM auth.
// Possible logic might take into consideration a threshold between
// the current player time and the DRM metadata start time. For the
// time being, we resolve it as soon as we receive the DRM metadata.

DRMManager drmManager = _mediaPlayer.getDRMManager(); if (drmManager == null) {
PMPDemoApp.logger.e(LOG_TAG +
"#onDRMMetadata", "DRMManager is null.");
return;
}

SharedPreferences sharedPreferences = PreferenceManager.getDefaultSharedPreferences(getActivity());
String authUser = sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_USERNAME,
getResources().getString(R.string.drmUsername));
String authPass = sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_PASSWORD,
getResources().getString(R.string.drmPassword));
DRMHelper.performDrmAuthentication(drmManager,
drmMetadataInfo.getDRMMetadata(), authUser,
authPass,
new DRMAuthenticationListener() {
@Override
public void onAuthenticationStart() { PMPDemoApp.logger.i(LOG_TAG +
"#onAuthenticationStart",
"DRM authentication started for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
@Override
public void onAuthenticationError(int major,
int minor,
String erroString, String serverErrorURL) {
if (getActivity() == null) { return;
}
PMPDemoApp.logger.e(LOG_TAG +
"#onAuthenticationError",
"DRM authentication failed. " + major +
" 0x" +
Long.toHexString(minor));
_handler.post(new Runnable() {
@Override
public void run() { showToast(getString(R.string.drmAuthenticationError)); getActivity().finish();
}
});
}
@Override
public void onAuthenticationComplete(byte[] authenticationToken) { PMPDemoApp.logger.i(LOG_TAG +
"#onAuthenticationComplete",
"Auth successful for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
});
}
};
```

La variable statique `DRMManager` L’instance disponible dans la version 1.4 après la création de Media Player est désormais disponible après la création de la fonction `onDRMMetadataInfo` l’écouteur d’événement est déclenché.

## Changements liés au débit adaptatif {#adaptive-bitrate-abr-related-changes}

**Modifications des constantes**

De nombreuses constantes ont changé de type `String` to `int`. Par exemple : `MediaResourceType`, `ABRControlParameters`, et `MediaPlayerStatusChangeEvent`.

```java
//TVSDK v1.4
ABRControlParameters
private void setAbrControlParams() { SharedPreferences sharedPreferences =
PreferenceManager.getDefaultSharedPreferences(getActivity());
if (sharedPreferences.getBoolean(PMPDemoApp.SETTINGS_ABR_CTRL_ENABLED,
PMPDemoApp.DEFAULT_ABR_ENABLED)) {
int initialBitRate = getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_INITIAL_BITRATE, 0);
int minBitRate = getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MIN_BITRATE, 0);
int maxBitRate = getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_BITRATE, PMPDemoApp.DEFAULT_MAX_BIT_RATE);
int mbrPolicyAsInt =
getIntPreference(sharedPreferences, PMPDemoApp.SETTINGS_ABR_POLICY, 0); ABRControlParameters.ABRPolicy abrPolicy = policyFromInt(mbrPolicyAsInt); abrPolicy = abrPolicy != null ?
abrPolicy : ABRControlParameters.ABRPolicy.ABR_MODERATE;
_mediaPlayer.setABRControlParameters(new ABRControlParameters(initialBitRate,
minBitRate, maxBitRate, abrPolicy));
}
}

//TVSDK v2.5
ABRControlParameters
private void setAbrControlParams() { ABRControlParametersBuilder abrBuilder =
new ABRControlParametersBuilder();

if (sharedPreferences.getBoolean(PMPDemoApp.SETTINGS_ABR_CTRL_ENABLED, PMPDemoApp.DEFAULT_ABR_ENABLED)) {

abrBuilder.setInitialBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_INITIAL_BITRATE,
ABRControlParameters.DEFAULT_ABR_INITIAL_BITRATE)); abrBuilder.setMinBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MIN_BITRATE,
ABRControlParameters.DEFAULT_ABR_MIN_BITRATE)); abrBuilder.setMaxBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_BITRATE,
ABRControlParameters.DEFAULT_ABR_MAX_BITRATE)); abrBuilder.setMaxPlayoutRate(getDoublePreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_PLAYOUT_RATE,
ABRControlParameters.DEFAULT_MAX_PLAYOUT_RATE)); abrBuilder.setMinTrickPlayBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MIN_TRICKPLAY_BITRATE,
ABRControlParameters.DEFAULT_ABR_MIN_BITRATE)); abrBuilder.setMaxTrickPlayBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_TRICKPLAY_BITRATE,
ABRControlParameters.DEFAULT_ABR_MAX_BITRATE)); abrBuilder.setMaxTrickPlayBandwidthUsage(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_TRICKPLAY_BANDWIDTH,
ABRControlParameters.DEFAULT_ABR_MAX_BITRATE));

switch (getIntPreference(sharedPreferences, PMPDemoApp.SETTINGS_ABR_POLICY, -1)) {
case 0: abrBuilder.setPolicy(ABRControlParameters.ABRPolicy.ABR_CONSERVATIVE); break;
case 1: abrBuilder.setPolicy(ABRControlParameters.ABRPolicy.ABR_MODERATE); break;
case 2: abrBuilder.setPolicy(ABRControlParameters.ABRPolicy.ABR_AGGRESSIVE); break;
default: abrBuilder.setPolicy(ABRControlParameters.DEFAULT_ABR_POLICY);
}
}
_mediaPlayer.setABRControlParameters(abrBuilder.toABRControlParameters());
}
```

**Modifications apportées au constructeur ABRControlParameters**

Certains paramètres ont été ajoutés, certains renommés et d’autres déplacés. Voici la signature du constructeur dans la version 1.4 et la nouvelle signature dans la version 2.5 :

```java
//TVSDK v1.4
public ABRControlParameters(ABRPolicy abrPolicy,
int nInitialBitRate, int nMinBitRate,
int nMaxBitRate)

//TVSDK v2.5
public ABRControlParameters(int nInitialBitRate,
int nMinBitRate, int nMaxBitRate,
ABRPolicy abrPolicy,
int nMinTrickPlayBitRate, int nMaxTrickPlayBitRate,
int nMaxTrickPlayBandwidthUsage, double dMaxPlayoutRate)
```

## Événements d’erreur et gestion {#error-events-and-handling}

**Modifications de la gestion des erreurs**

La variable `MediaError` a été remplacé par la classe `Notification` classe . La seule différence entre les classes `MediaError` et `Notification` est que ce dernier ne contient pas d’attribut de description. Les codes d’erreur TVSDK 1.4 avec les valeurs 101xxx, 102xxx,104xxx,106xxx,107xxx,109xxx n’existent pas dans TVSDK 2.5. Pour connaître les codes de lecture de TVSDK 2.5, voir [Erreur native - Valeurs de lecture vidéo](assets/psdk_android_2.5.pdf).

Vous trouverez ci-dessous des exemples de gestion des erreurs dans TVSDK 1.4 et 2.5 :

```java
//TVSDK v1.4
@Override
public void onStateChanged(MediaPlayer.PlayerState state, MediaPlayerNotification notification) {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Player state changed to [" + state
+ "].");

switch (state) {
// Non recoverable state - either reset player and reinitialize
// or release the player and create a new one.
case ERROR: PMPDemoApp.logger.e(LOG_TAG +
"::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Error: " + notification + "."); getActivity().finish();
break;
default:
// do nothing
}
}

//TVSDK v2.5
private final StatusChangeEventListener statusChangeEventListener = new StatusChangeEventListener() {
@Override
public void onStatusChanged(MediaPlayerStatusChangeEvent mediaPlayerStatusChangeEvent)
{
MediaPlayerStatus state = mediaPlayerStatusChangeEvent.getStatus(); PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Player state changed to [" + state
+ "].");
switch (state) {
// Non recoverable state - either reset player and reinitialize
// or release the player and create a new one.
case ERROR:
PMPDemoApp.logger.e(LOG_TAG + "::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Error: ");
printErrorMetadata(mediaPlayerStatusChangeEvent.getMetadata()); showToast("MediaPlayer status ERROR: Look at the logs for details"); getActivity().finish();
break;
default:
// do nothing
}
}
};
```

Toutes les erreurs récupérables sont traitées comme des avertissements et sont traitées à l’aide de la variable `NotificationEventListener` dans TVSDK 2.5. Les avertissements s’affichent sous forme de notifications avec la fonction `onOperationFailed` Écouteur dans le gestionnaire QOS dans TVSDK 1.4 où, comme dans TVSDK 2.5, la notification est un événement distinct. L’avertissement traité dans les versions 1.4 et 2.5 est le suivant :

```java
//TVSDK v1.4
private final MediaPlayer.QOSEventListener _qosEventListener = new MediaPlayer.QOSEventListener()
{
@Override
public void onBufferStart() {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onBufferStart()", "Buffering started.");
}
@Override
public void onBufferComplete() {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onBufferComplete()", "Buffering complete.");
}
@Override
public void onSeekStart() {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onSeekStart()", "Seek starting.");
}
@Override
public void onSeekComplete(long adjustedTime) {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onSeekComplete()", "Seek complete at position: " + adjustedTime + ".");
}
@Override
public void onLoadInfo(LoadInfo loadInfo) {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onLoadInfo()", "Url: " + loadInfo.getUrl() + ", size: "
+ loadInfo.getSize() + " bytes, media duration: " + loadInfo.getMediaDuration() + "ms, download duration: " + loadInfo.getDownloadDuration() + "ms");
}
@Override
public void onOperationFailed(MediaPlayerNotification.Warning warning) {

StringBuffer sb = new StringBuffer("Player operation failed: "); sb.append(warning.getCode()).append(" - ").append(warning.getDescription()); if (warning.getMetadata() != null) {
sb.append("Warning metadata: ").append(warning.getMetadata().toString());
}

MediaPlayerNotification innerNotification = warning.getInnerNotification(); registerFailedAudioTrackIndex(innerNotification); handleFailedSeekEvent(innerNotification);

while (innerNotification != null) { sb.append("Inner notification: ");
sb.append(innerNotification.getCode()).append(" - ").append(innerNotification.getDescription());
Metadata metadata = innerNotification.getMetadata(); if (metadata != null) {
for (String key : metadata.keySet()) { sb.append(" - ").append

//TVSDK v2.5
private final NotificationEventListener notificationEventListener = new NotificationEventListener() {
/**
* An example of dumping the information within a Notification. Here, we don't handle the event in
* any way except to print a log message.
* @param event The NotificationEvent
*/
@Override
public void onNotification(NotificationEvent event) { Notification notification = event.getNotification(); Notification.Type type = notification.getType(); StringBuilder sb = new StringBuilder(); sb.append("[").append(type).append("]");
sb.append(" Player operation failed (").append(notification.getCode()).append(")"); Metadata metadata = notification.getMetadata();
if (metadata != null)
{
for (String key : metadata.keySet())
{
sb.append(", ").append(key).append(" = ").append(metadata.getValue(key));
}
}
Notification inner = notification.getInnerNotification(); if (inner != null) {
sb.append(" :: Inner Notification [").append(inner.getType()).append("](").append(inner.getCode()).append(")");
Metadata innerMetadata = inner.getMetadata(); if (innerMetadata != null) {
for (String iKey : innerMetadata.keySet()) { sb.append(", ").append(iKey).append(" =
").append(innerMetadata.getValue(iKey));
}
}
}
switch(type)
{
case ERROR:
PMPDemoApp.logger.e(LOG_TAG, sb.toString()); break;
case WARNING:
PMPDemoApp.logger.w(LOG_TAG, sb.toString()); break;
default:
PMPDemoApp.logger.i(LOG_TAG, sb.toString()); break;
}
showToast(sb.toString()); PMPDemoApp.logger.d(LOG_TAG, sb.toString());
}
};
```

**Nouvelles exceptions**

Tandis que TVSDK v1.4 utilisait une combinaison de valeurs nulles, de retours d’erreur et de diverses exceptions ( `MediaPlayerException`, `IllegalStateException`, et `IllegalArgumentException`), TVSDK v2.5 `generatesMediaPlayerException` pour toutes les erreurs.

>[!NOTE]
>
>Pour obtenir des détails sur une exception MediaPlayerException, vous pouvez utiliser `getErrorCode()`.

Voici un exemple de modification :

```java
//TVSDK v1.4
public void setBufferControlParams() { try {
mediaPlayer.setBufferControlParameters(getBufferParamsFromSettings());
} catch (IllegalArgumentException e) { PrimetimeReference.logger.w(LOG_TAG +
"#setBufferControlParams",
"Unable to apply buffering params: " + e.getMessage() + ".");
}
}

//TVSDK v2.5
public void setBufferControlParams() { try {
mediaPlayer.setBufferControlParameters(getBufferParamsFromSettings());
} catch (MediaPlayerException e) { PrimetimeReference.logger.w(LOG_TAG + "#setBufferControlParams", "Unable to apply buffering params: " + e.getMessage() + ".");
}
}
```

## Modifications des paramètres QOS {#changes-to-qos-parameters}

Des modifications mineures ont été apportées aux propriétés de l’objet QOSProvider :

* La variable `TimeToFirstFrame` n’est pas disponible dans TVSDK 2.5.
* TVSDK 2.5 QOSProvider possède une nouvelle propriété pour déterminer la bande passante perçue lors d’une session de diffusion en continu.

```java
//TVSDK v1.4
public void updateQosInformation(PlaybackInformation playbackInformation) { if (playbackInformation == null) {
return;
}
setQosItem("Frame rate", (int) playbackInformation.getFrameRate() +
" (" + (int) playbackInformation.getDroppedFrameCount() + " dropped)"); setQosItem("Bitrate", (int) playbackInformation.getBitrate()); setQosItem("Buffering time", (long) playbackInformation.getBufferingTime()); setQosItem("Buffer length", (long) playbackInformation.getBufferLength()); setQosItem("Buffer time", (long) playbackInformation.getBufferTime()); setQosItem("Empty buffer count", (int) playbackInformation.getEmptyBufferCount()); setQosItem("Time to load", (int) playbackInformation.getTimeToLoad()); setQosItem("Time to start", (int) playbackInformation.getTimeToStart()); setQosItem("Time to first frame", (int) playbackInformation.getTimeToFirstFrame()); setQosItem("Time to prepare", (int) playbackInformation.getTimeToPrepare()); setQosItem("Last seek time", (int) playbackInformation.getLastSeekTime());
}

//TVSDK v2.5
public void updateQosInformation(PlaybackInformation playbackInformation) { if (playbackInformation == null) {
return;
}
setQosItem("Frame rate", (int) playbackInformation.getFrameRate() +
" (" + (int) playbackInformation.getDroppedFrameCount() + " dropped)"); setQosItem("Bitrate", (int) playbackInformation.getBitRate()); setQosItem("Buffering time", (long) playbackInformation.getBufferingTime()); setQosItem("Buffer length", (long) playbackInformation.getBufferLength()); setQosItem("Buffer time", (long) playbackInformation.getBufferTime()); setQosItem("Empty buffer count", (int) playbackInformation.getEmptyBufferCount()); setQosItem("Time to load", (int) playbackInformation.getTimeToLoad()); setQosItem("Time to start", (int) playbackInformation.getTimeToStart());
setQosItem("Time to prepare", (int) playbackInformation.getTimeToPrepare());
setQosItem("Perceived Bandwidth", (int) playbackInformation.getPerceivedBandwidth());
```

* La variable `QOSEventListener::onOperationFailed()` n’existe plus dans TVSDK 2.5. Les avertissements qui apparaissaient auparavant dans ce programme d’écoute d’événement apparaissent désormais dans la variable `NotificationEventListener::onNotification()` écouteur d’événement.

* La variable `QOSProvider event listeners onBufferStart()`, `onBufferComplete()`, `onSeekStart()`, `onSeekComplete()`, et `onLoadInfo()` sont des écouteurs d’événements individuels liés à une instance mediaPlayer.

```java
//TVSDK v1.4
private final MediaPlayer.QOSEventListener _qosEventListener = new MediaPlayer.QOSEventListener() {

@Override
public void onBufferStart() { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferStart()", "Buffering started.");
showBufferingSpinner();
}
@Override
public void onBufferComplete() { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferComplete()", "Buffering complete.");
hideBufferingSpinner();
}
@Override
public void onSeekStart() { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekStart()", "Seek starting.");
inTrickPlayMode = false;
}
@Override
public void onSeekComplete(long adjustedTime) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekComplete()", "Seek complete at position: " +
adjustedTime + ".");
_controlBar.setPosition(adjustedTime);
if (adjustedTime == _mediaPlayer.getPlaybackRange().getEnd() &&
_mediaPlayer.getStatus() == MediaPlayer.PlayerState.COMPLETE) {
// Show the replay button. showReplayButton();
}
if (_mediaPlayer.getStatus() == MediaPlayer.PlayerState.PAUSED) {
// Show the pause icon.
_controlBar.pause();
}
}
@Override
public void onLoadInfo(LoadInfo loadInfo) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onLoadInfo()", "Url: " +
loadInfo.getUrl() + ", size: " + loadInfo.getSize() +
" bytes, media duration: " +
loadInfo.getMediaDuration() + "ms, download duration: " +
loadInfo.getDownloadDuration() + "ms");
 
public void onOperationFailed(MediaPlayerNotification.Warning warning) {

StringBuffer sb = new StringBuffer("Player operation failed: "); sb.append(warning.getCode()).append(" - ").append(warning.getDescription()); if (warning.getMetadata() != null) {
sb.append("Warning metadata: ").append(warning.getMetadata().toString());
}

MediaPlayerNotification innerNotification = warning.getInnerNotification(); registerFailedAudioTrackIndex(innerNotification); handleFailedSeekEvent(innerNotification);

while (innerNotification != null) { sb.append("Inner notification: ");
sb.append(innerNotification.getCode()).append(" - "). append(innerNotification.getDescription());
Metadata metadata = innerNotification.getMetadata(); if (metadata != null) {
for (String key : metadata.keySet()) { sb.append(" - ").append(key).append(": ").
append(metadata.getValue(key));
}
}
innerNotification = innerNotification.getInnerNotification();
}
String errMsg = sb.toString(); PMPDemoApp.logger.w(LOG_TAG +
"::MediaPlayer.QOSEventListener#onOperationFailed()", errMsg);
showToast(errMsg);
}
};

//TVSDK v2.5
mediaPlayer.addEventListener(MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE,
loadInfoEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.BUFFERING_BEGIN,
bufferingBeginEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.BUFFERING_END,
bufferingEndEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.SEEK_BEGIN,
seekBeginEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.SEEK_END,
seekEndEventListener);
// Buffering events.
BufferingBeginEventListener bufferingBeginEventListener = new BufferingBeginEventListener() {
@Override
public void onBufferingBegin(BufferEvent bufferEvent) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferStart()", "Buffering started.");
showBufferingSpinner();
}
};

BufferingEndEventListener bufferingEndEventListener = new BufferingEndEventListener() {
@Override
public void onBufferingEnd(BufferEvent bufferEvent) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferComplete()",
"Buffering complete."); hideBufferingSpinner();
}
};

BufferPreparedEventListener bufferPreparedEventListener = new BufferPreparedEventListener() {
@Override
public void onBufferPrepared() {
}
};
// seek events.
SeekBeginEventListener seekBeginEventListener = new SeekBeginEventListener() {

@Override
public void onSeekBegin(SeekEvent seekEvent) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekStart()", "Seek starting.");
inTrickPlayMode = false;
}
};
SeekEndEventListener seekEndEventListener = new SeekEndEventListener() {
@Override
public void onSeekEnd(SeekEvent seekEvent) {
double adjustedTime = seekEvent.getActualPosition();
PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekComplete()", "Seek complete at position: " + adjustedTime + ".");
_controlBar.setPosition((long) adjustedTime);
if (adjustedTime == _mediaPlayer.getPlaybackRange().getEnd() &&
_mediaPlayer.getStatus() == MediaPlayerStatus.COMPLETE) {
// Show the replay button. showReplayButton();
}
if (_mediaPlayer.getStatus() == MediaPlayerStatus.PAUSED) {
// Show the pause icon.
_controlBar.pause();
}
}
};
/**
* LoadInformationEventListener that intercepts PSDK load info events
*/
private final LoadInformationEventListener loadInfoEventListener = new LoadInformationEventListener() {

@Override
public void onLoadInformation(LoadInformationEvent event) { LoadInformation loadInfo = event.getLoadInfomation(); PMPDemoApp.logger.i(
LOG_TAG + "::LoadInformationEventListener#onLoadInfomation()", "Url: " + loadInfo.getUrl() + ", size: "
+ loadInfo.getSize()
+ " bytes, download duration: "
+ loadInfo.getDownloadDuration() + "ms");
}
};
```

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://helpx.adobe.com/support/primetime.html) page.
