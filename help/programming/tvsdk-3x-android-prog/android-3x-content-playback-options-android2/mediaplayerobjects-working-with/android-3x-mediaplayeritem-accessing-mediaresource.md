---
description: Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.
title: Méthodes MediaPlayerItem pour accéder aux informations MediaResource
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Méthodes MediaPlayerItem pour accéder aux informations MediaResource {#mediaplayeritem-methods-for-accessing-mediaresource-information}

Les méthodes de la classe MediaPlayerItem vous permettent d’obtenir des informations sur le flux de contenu représenté par une ressource MediaResource chargée.

| Méthode | Description |
|--- |--- |
| **Balises publicitaires** |  |
| Liste`<String>` getAdTags() | Fournit la liste des balises d’annonce utilisées pour le processus d’emplacement des publicités. |
| **Flux en direct** |  |
| boolean isLive(); | True si le flux est actif ; false s’il est VOD. |
| **DRM protégé** |  |
| boolean isProtected(); | True si le flux est protégé par DRM. |
| Liste`<DRMMetadataInfo>` getDRMMetadataInfos(); | Répertorie tous les objets de métadonnées DRM découverts dans le manifeste. |
| **Sous-titres codés** |  |
| boolean hasClosedCaptions(); | True si des pistes de sous-titres sont disponibles. |
| Liste`<ClosedCaptionsTrack>` getClosedCationsTracks(); | Fournit une liste des suivis de sous-titres disponibles. |
| ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); | Récupère le suivi actuel des sous-titres sélectionnés avec SelectClosedCaptionsTrack . |
| selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack) | Définit un suivi de sous-titres comme suivi de sous-titres fermés actuel. |
| **Autres pistes audio** |  |
| boolean hasAlternateAudio(); | True si le flux comporte des pistes audio alternatives. Remarque : La piste audio principale (par défaut) fait également partie de la liste de piste audio alternative.  TVSDK pour Android considère la piste audio principale comme l’un des éléments de la liste de piste audio alternative. Pour cette raison, le seul cas où MediaPlayerItem.hasAlternateAudio renvoie false est le cas où le flux ne comporte pas de contenu audio. Si le contenu ne comporte qu’une seule piste audio, cette méthode renvoie la valeur true et  `MediaPlayerItem.getAudioTracks`  renvoie une liste avec un seul élément (la piste audio par défaut). |
| Liste`<AudioTrack>` getAudioTracks(); | Fournit une liste des pistes audio secondaires disponibles. |
| AudioTrack getSelectedAudioTrack(); | Récupère la piste audio sélectionnée avec selectAudioTrack . |
| selectAudioTrack ( AudioTrack audioTrack ) | Permet de sélectionner une piste audio comme piste audio actuelle. |
| **Métadonnées minutées** |  |
| booléen hasTimedMetadata(); | True si le flux a associé des métadonnées minutées. |
| Liste`<TimedMetadata>` getTimedMetadata(); | Fournit une liste des objets de métadonnées minutés associés au flux. |
| **Profils multiples (débit)** |
| boolean isDynamic(); | True si le flux est un flux à débit multiple (MBR). |
| Liste`<Profile>` getProfiles(); | Fournit une liste des profils de débit associés. Pour chaque profil, vous pouvez récupérer son débit ainsi que la hauteur et la largeur du profil. |
| Profile getSelectedProfile() | Récupère le profil actuellement sélectionné. |
| **Lecture de piste** |  |
| booléen isTrickPlaySupported(); | True si le lecteur prend en charge l’avance rapide, le retour arrière et la reprise. |
| Liste`< Float>` getAvailablePlaybackRates() | Fournit la liste des taux de lecture disponibles dans le contexte de la fonction de lecture de l’astuce. |
| Float getSelectedPlaybackRate() | Récupère le taux de lecture actuellement sélectionné. |
| MediaPlayerItemConfig getConfig() | Renvoie l’instance MediaPlayerItemConfig associée à cet élément. |
| **Ressource multimédia** |  |
| MediaResource getResource(); | Renvoie la ressource multimédia associée à cet élément. |
| int getResourceId() | Renvoie l’identifiant du média associé à cet élément. Cet identifiant est défini lorsque l’élément est chargé à l’aide de MediaPlayerItemLoader.load . |
