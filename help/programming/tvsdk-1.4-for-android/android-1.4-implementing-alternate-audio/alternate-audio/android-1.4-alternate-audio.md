---
description: Le son alternatif, ou à liaison tardive, vous permet de basculer entre les pistes audio disponibles pour une piste vidéo. Ainsi, les utilisateurs peuvent sélectionner un suivi de langue lors de la lecture de la vidéo.
seo-description: Le son alternatif, ou à liaison tardive, vous permet de basculer entre les pistes audio disponibles pour une piste vidéo. Ainsi, les utilisateurs peuvent sélectionner un suivi de langue lors de la lecture de la vidéo.
seo-title: Autre son
title: Autre son
uuid: 0abd727c-7036-49c5-a4b7-8945711fecc8
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Autre son {#alternate-audio}

Le son alternatif, ou à liaison tardive, vous permet de basculer entre les pistes audio disponibles pour une piste vidéo. Ainsi, les utilisateurs peuvent sélectionner un suivi de langue lors de la lecture de la vidéo.

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

Lorsque TVSDK crée l’ `MediaPlayerItem` instance de la vidéo active, il crée un `AudioTrack` élément pour chaque piste audio disponible. L’élément contient une `name` propriété, une chaîne contenant généralement une description reconnaissable par l’utilisateur de la langue de ce suivi. L’élément contient également des informations sur l’utilisation de ce suivi par défaut.

Quand il est temps de lire la vidéo, vous pouvez demander une liste des pistes audio disponibles, laisser l&#39;utilisateur en choisir une, et configurer la lecture de la vidéo pour la lecture avec la piste sélectionnée.

Bien que rare, si une piste audio supplémentaire devient disponible après sa création `MediaPlayerItem`, TVSDK déclenche un `MediaPlayerItem.AUDIO_UPDATED` événement.

## Ajout d’API {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}

Les API suivantes ont été ajoutées pour prendre en charge les fichiers audio alternatifs :

`hasAlternateAudio`

Si le média spécifié comporte une autre piste audio, autre que la piste par défaut, cette fonction booléenne renvoie `true`. S’il n’existe aucune autre piste audio, la fonction renvoie `false`.

```
bool MediaPlayerItemImpl::hasAlternateAudio() const { 
    return _hasAlternateAudio; 
}
```

** `getAudioTracks`**

Cette fonction renvoie la liste de toutes les pistes audio actuellement disponibles dans un média spécifié.

```
virtual PSDKErrorCode getAudioTracks(PSDKImmutableArray<AudioTrack>*& out) const { 
if (_audioTracks) { 
    out = _audioTracks; 
    out->addRef(); 
    return kECSuccess; 
    } 
    return kECDataNotAvailable; 
} 
```

`getSelectedAudioTrack`

Cette fonction renvoie les autres propriétés et pistes audio actuellement sélectionnées, telles que la langue. La sélection automatique de la piste peut également être extraite.

```
PSDKErrorCode MediaPlayerItemImpl::getSelectedAudioTrack(AudioTrack &out) const { 
    out = _currentAudioTrack; 
    return kECSuccess; 
}
```

`selectAudioTrack`

Cette fonction sélectionne une autre piste audio à lire.

```
PSDKErrorCode MediaPlayerItemImpl::selectAudioTrack(const AudioTrack &audioTrack) { 
    _lastPlayedAudioTrack = _currentAudioTrack; 
    if(_mediaPlayer && _mediaPlayer->_trickPlay) 
        return kECUnsupportedOperation; 
    _currentAudioTrack = audioTrack; 
    PSDKErrorCode result = kECSuccess; 
    if (_currentAudioTrack) { 
        media::TimeLine* timeline = NULL; 
        if (_mediaPlayer->_fragHttpStreamer) 
            _mediaPlayer->_fragHttpStreamer->GetTimeLine(&timeline); 
        if (timeline) { 
            for (int32_t i = timeline->GetFirstPeriodIndex(); i <= timeline->GetLastPeriodIndex(); i++){ 
                media::ErrorCode error = selectTrack(timeline,_mediaPlayer->_fragHttpStreamer, i, audioTrack.getName(), media::kSTTAudioIndex); 
                return _mediaPlayer->convertToPSDKError(error); 
            } 
        } 
    }   
    return result; 
}
```

