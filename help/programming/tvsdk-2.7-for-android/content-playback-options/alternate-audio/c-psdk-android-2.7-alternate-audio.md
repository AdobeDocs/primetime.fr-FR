---
description: L’audio de remplacement vous permet de basculer entre les pistes audio disponibles pour une piste vidéo. Les utilisateurs peuvent sélectionner la langue de leur choix lors de la lecture de la vidéo.
seo-description: L’audio de remplacement vous permet de basculer entre les pistes audio disponibles pour une piste vidéo. Les utilisateurs peuvent sélectionner la langue de leur choix lors de la lecture de la vidéo.
seo-title: Autre son
title: Autre son
uuid: 86aa5393-6a9e-49db-807b-7299e6b4ab2b
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---


# Aperçu {#alternate-audio-overview}

L’audio de remplacement vous permet de basculer entre les pistes audio disponibles pour une piste vidéo. Les utilisateurs peuvent sélectionner la langue de leur choix lors de la lecture de la vidéo.

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

Lorsque TVSDK crée l’instance `MediaPlayerItem` pour la vidéo en cours, il crée un élément `AudioTrack` pour chaque piste audio disponible. L’élément contient une propriété `name`, qui est une chaîne contenant généralement une description reconnaissable par l’utilisateur de la langue de ce suivi. L’élément contient également des informations sur l’utilisation de ce suivi par défaut. Lorsqu&#39;il est temps de lire la vidéo, vous pouvez demander une liste des pistes audio disponibles, éventuellement permettre à l&#39;utilisateur de sélectionner une piste, et définir la lecture de la vidéo avec la piste sélectionnée.

>[!TIP]
>
>Bien que rare, si une autre piste audio devient disponible après que TVSDK a créé le `MediaPlayerItem`, TVSDK déclenche un événement `MediaPlayerItem.AUDIO_TRACK_UPDATED`.

## API Ajoutées {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}

Les API suivantes ont été ajoutées pour prendre en charge les fichiers audio alternatifs :

`hasAlternateAudio`

Si le média spécifié possède une autre piste audio, autre que la piste par défaut, cette fonction booléenne renvoie `true`. S&#39;il n&#39;existe aucune autre piste audio, la fonction renvoie `false`.

```java
boolean hasAlternateAudio();
```

** `getAudioTracks`**

Cette fonction renvoie la liste de toutes les pistes audio actuellement disponibles dans un média spécifié.

```java
List<AudioTrack> getAudioTracks();
```

`getSelectedAudioTrack`

Cette fonction renvoie les autres propriétés et pistes audio actuellement sélectionnées, telles que la langue. La sélection automatique de la piste peut également être extraite.

```java
AudioTrack getSelectedAudioTrack();
```

`selectAudioTrack`

Cette fonction sélectionne une autre piste audio à lire.

```java
void selectAudioTrack(AudioTrack audioTrack);
```

Par exemple :

```java
private void onPrepared() { 
    // Select the AA track in PREPARED State 
    boolean hasAlternateAudio = _mediaPlayer.getCurrentItem().hasAlternateAudio(); 
    if(hasAlternateAudio) { 
        AudioTrack selectedAudioTrack =  
          _mediaPlayer.getCurrentItem().getSelectedAudioTrack(); 
 
        if (selectedAudioTrack == null) {  
            // Selecting default audio track  
            // If index is 1 it will select alternate audio track  
            selectedAudioTrack = _mediaPlayer.getCurrentItem().getAudioTracks().get(0);  
        } 
    } 
    _mediaPlayer.getCurrentItem().selectAudioTrack(selectedAudioTrack); 
} 
```

