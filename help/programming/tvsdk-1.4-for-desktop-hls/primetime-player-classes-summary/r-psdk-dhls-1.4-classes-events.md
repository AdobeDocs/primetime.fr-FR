---
description: Ces classes décrivent les événements distribués par TVSDK à votre lecteur multimédia en réponse à diverses activités.
title: Classes d’événements
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Classes d’événements {#events-classes}

Ces classes décrivent les événements distribués par TVSDK à votre lecteur multimédia en réponse à diverses activités.

Package : [com.adobe.mediacore.events](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/package-detail.html)

| Nom | Signification |
|---|---|
| [AdBreakPlaybackEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html) | Classe. Une coupure publicitaire a commencé ou s’est terminée. |
| [AdClickEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html) | Classe. L’utilisateur a cliqué sur une publicité. |
| [AdPlaybackEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html) | Classe. Le lecteur a joué une publicité. |
| [BufferEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html) | Classe. Le lecteur a démarré ou arrêté la mise en mémoire tampon. |
| [CustomAdEvent](https://experienceleague.adobe.com/docs/primetime/programming/tvsdk-1-4-for-desktop-hls/advertising/custom-ads/r-psdk-dhls-1.4-custom-ad-events.html?lang=en) | Classe. Le lecteur affiche le statut de chargement des publicités personnalisées et peut ignorer les publicités qui comportent des erreurs ou dont le chargement prend trop de temps. |
| [DRMMetadataInfoEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html) | Classe. Les nouvelles métadonnées DRM sont associées à l’élément actif. |
| [LoadInformationEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/LoadInformationEvent.html) | Classe. Des informations de téléchargement sont disponibles pour le flux multimédia en cours de lecture. |
| [MediaPlayerItemEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html) | Classe. Un élément du lecteur multimédia a été créé. |
| [MediaPlayerItemLoaderEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemLoaderEvent.html) | Classe. Une opération de chargement est terminée. Distribué par `MediaPlayerItemLoader` pour notifier ses clients. |
| [MediaPlayerStatusChangeEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerStatusChangeEvent.html) | Classe. Le statut du lecteur multimédia a changé. |
| [MediaPlayerViewEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerViewEvent.html) | Classe. La variable `MediaPlayerView` a été cliqué. |
| [PlaybackRateEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html) | Classe. Le taux de lecture du lecteur multimédia change. |
| [ProfileEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/ProfileEvent.html) | Classe. L’algorithme de changement de débit adaptatif du lecteur multimédia est passé à un autre profil en raison des conditions réseau ou machine. |
| [SeekEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html) | Classe. Le lecteur a commencé la recherche ou l’opération de recherche s’est terminée. |
| [SizeAvailableEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SizeAvailableEvent.html) | Classe. La taille de la vidéo est disponible. |
| [TimeChangeEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimeChangeEvent.html) | Classe. Le statut du lecteur multimédia a changé. |
| [TimedMetadataEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html) | Classe. Une métadonnée minutée est traitée par le détecteur d’opportunités. |
| [TimelineEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html) | Classe. La chronologie du lecteur multimédia a changé. |
