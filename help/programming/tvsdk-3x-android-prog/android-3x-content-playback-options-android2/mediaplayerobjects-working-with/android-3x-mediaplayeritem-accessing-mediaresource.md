---
description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
seo-description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
seo-title: Méthodes MediaPlayerItem pour accéder aux informations MediaResource
title: Méthodes MediaPlayerItem pour accéder aux informations MediaResource
uuid: 46845583-0a76-4411-a8bc-0a16ebfe8e6e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---


# Méthodes MediaPlayerItem pour accéder aux informations MediaResource {#mediaplayeritem-methods-for-accessing-mediaresource-information}

Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.

| Méthode | Description |
|--- |--- |
| **Balises publicitaires** |  |
| Liste`<String>` getAdTags() | Fournit la liste des balises publicitaires utilisées pour le processus d’emplacement des publicités. |
| **Flux en direct** |  |
| booléen isLive(); | True si le flux est actif ; false s’il s’agit de VOD. |
| **DRM protégé** |  |
| booléen isProtected(); | True si le flux est protégé par DRM. |
| Liste`<DRMMetadataInfo>` getDRMMetadataInfos(); | Liste tous les objets de métadonnées DRM découverts dans le manifeste. |
| **Sous-titres** |  |
| booléen hasClosedCaptions(); | True si des pistes de sous-titrage sont disponibles. |
| Liste`<ClosedCaptionsTrack>` getClosedCationsTracks(); | Fournit une liste de pistes de sous-titres disponibles. |
| ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); | Récupère le suivi de sous-titrage actuel sélectionné avec SelectClosedCaptionsTrack. |
| selectClosedCaptionsTrack ( ClosedCaptionsTrack ClosedCaptionsTrack) | Définit une piste de sous-titrage fermée comme piste de sous-titrage fermée actuelle. |
| **Autres pistes audio** |  |
| booléen hasAlternateAudio(); | True si le flux comporte d’autres pistes audio. Remarque :  La piste audio principale (par défaut) fait également partie de la liste de piste audio alternative.  TVSDK pour Android considère la piste audio principale comme l’un des éléments de la liste de piste audio alternative. Par conséquent, le seul cas où MediaPlayerItem.hasAlternateAudio renvoie false est celui où le flux n’a pas de son du tout. Si le contenu ne comporte qu’une seule piste audio, cette méthode renvoie true et `MediaPlayerItem.getAudioTracks` renvoie une liste avec un seul élément (la piste audio par défaut). |
| Liste`<AudioTrack>` getAudioTracks(); | Fournit une liste de pistes audio alternatives disponibles. |
| AudioTrack getSelectedAudioTrack(); | Récupère la piste audio sélectionnée avec selectAudioTrack. |
| selectAudioTrack ( AudioTrack audioTrack ) | Sélectionne une piste audio à utiliser comme piste audio actuelle. |
| **Métadonnées minutées** |  |
| booléen hasTimedMetadata(); | True si le flux est associé à des métadonnées temporisées. |
| Liste`<TimedMetadata>` getTimedMetadata(); | Fournit une liste des objets de métadonnées minutés associés au flux. |
| **Plusieurs profils (débit)** |
| booléen isDynamic(); | True si le flux est un flux à débit binaire multiple (MBR). |
| Liste`<Profile>` getProfiles(); | Fournit une liste des profils de débit binaire associés. Pour chaque profil, vous pouvez récupérer son débit ainsi que la hauteur et la largeur du profil. |
| Profil getSelectedProfile() | Récupère le profil actuellement sélectionné. |
| **Jeu de cartes** |  |
| booléen isTrickPlaySupported(); | True si le lecteur prend en charge l’avance rapide, le rembobinage et la reprise. |
| Liste`< Float>` getAvailablePlaybackRates() | Fournit la liste des taux de lecture disponibles dans le contexte de la fonction de lecture par astuces. |
| Float getSelectedPlaybackRate() | Récupère le taux de lecture actuellement sélectionné. |
| MediaPlayerItemConfig getConfig() | Renvoie l’instance MediaPlayerItemConfig associée à cet élément. |
| **Ressource média** |  |
| MediaResource getResource(); | Renvoie la ressource média associée à cet élément. |
| int getResourceId() | Renvoie l&#39;identifiant de média associé à cet élément. Cet ID est défini lorsque l’élément est chargé à l’aide de MediaPlayerItemLoader.load. |