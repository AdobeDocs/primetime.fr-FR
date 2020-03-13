---
description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
seo-description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
seo-title: Méthodes MediaPlayerItem pour l’accès aux informations MediaResource
title: Méthodes MediaPlayerItem pour l’accès aux informations MediaResource
uuid: 46845583-0a76-4411-a8bc-0a16ebfe8e6e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Méthodes MediaPlayerItem pour l’accès aux informations MediaResource {#mediaplayeritem-methods-for-accessing-mediaresource-information}

Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.

| Méthode | Description |
|--- |--- |
| **Balises publicitaires** |  |
| `<String>` getAdTags() | Fournit le des balises publicitaires utilisées pour le processus d’emplacement des publicités. |
| **Flux en direct** |  |
| booléen isLive(); | True si le flux est en direct ; false s’il s’agit de VOD. |
| **DRM protégé** |  |
| booléen isProtected(); | True si le flux est protégé par DRM. |
| `<DRMMetadataInfo>` getDRMMetadataInfos(); | tous les objets de métadonnées DRM découverts dans le manifeste. |
| **Sous-titres** |  |
| booléen hasClosedCaptions(); | True si des pistes de sous-titrage sont disponibles. |
| `<ClosedCaptionsTrack>` getClosedCationsTracks(); | Fournit un  de pistes de sous-titrage codé disponibles. |
| ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); | Récupère le suivi de sous-titrage actuel sélectionné avec SelectClosedCaptionsTrack. |
| selectClosedCaptionsTrack ( ClosedCaptionsTrack closeCaptionsTrack) | Définit une piste de sous-titrage codé comme la piste de sous-titrage codé actuelle. |
| **Autres pistes audio** |  |
| booléen hasAlternateAudio(); | True si le flux comporte des pistes audio de remplacement. Remarque :  La piste audio principale (par défaut) fait également partie du de piste audio alternatif.  TVSDK pour Android considère la piste audio principale comme l’un des éléments du de piste audio alternatif. Pour cette raison, le seul cas où MediaPlayerItem.hasAlternateAudio renvoie false est le cas où le flux n’a aucun son. Si le contenu ne comporte qu’une seule piste audio, cette méthode renvoie true et `MediaPlayerItem.getAudioTracks` renvoie un avec un seul élément (la piste audio par défaut). |
| `<AudioTrack>` getAudioTracks(); | Fournit un  de pistes audio alternatives disponibles. |
| AudioTrack getSelectedAudioTrack(); | Récupère la piste audio sélectionnée avec selectAudioTrack . |
| selectAudioTrack ( AudioTrack audioTrack ) | Sélectionne une piste audio à utiliser comme piste audio actuelle. |
| **Métadonnées minutées** |  |
| booléen hasTimedMetadata(); | True si le flux est associé à des métadonnées temporisées. |
| `<TimedMetadata>` getTimedMetadata(); | Fournit un des objets de métadonnées minutés associés au flux. |
| **multiples (débit)** |
| booléen isDynamic(); | True si le flux est un flux à débit binaire multiple (MBR). |
| `<Profile>` getProfiles(); | Fournit un  du de débit binaire associé. Pour chaque  de, vous pouvez récupérer son débit ainsi que la hauteur et la largeur du  de. |
| getSelectedProfile() | Récupère le  actuellement sélectionné. |
| **Trump play** |  |
| booléen isTrickPlaySupported(); | True si le lecteur prend en charge l’avance rapide, le rembobinage et la reprise. |
| `< Float>` getAvailablePlaybackRates() | Fournit le des taux de lecture disponibles dans le contexte de la fonction de lecture par astuce. |
| Float getSelectedPlaybackRate() | Récupère le taux de lecture actuellement sélectionné. |
| MediaPlayerItemConfig getConfig() | Renvoie l’instance MediaPlayerItemConfig associée à cet élément. |
| **Ressource média** |  |
| MediaResource getResource(); | Renvoie la ressource média associée à cet élément. |
| int getResourceId() | Renvoie l’identifiant de média associé à cet élément. Cet ID est défini lorsque l’élément est chargé à l’aide de MediaPlayerItemLoader.load. |