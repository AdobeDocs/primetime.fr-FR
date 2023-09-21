---
description: L’audio secondaire vous permet de passer d’une piste audio disponible à une autre. Les utilisateurs peuvent sélectionner la langue souhaitée pour la lecture de la vidéo.
title: Autre son
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Présentation {#alternate-audio-overview}

L’audio secondaire vous permet de passer d’une piste audio disponible à une autre. Les utilisateurs peuvent sélectionner la langue souhaitée pour la lecture de la vidéo.

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

Lorsque TVSDK crée la variable `MediaPlayerItem` pour la vidéo en cours, une `AudioTrack` pour chaque piste audio disponible. L’élément contient un `name` , qui est une chaîne qui contient généralement une description reconnaissable par l’utilisateur de la langue de ce suivi. L’élément contient également des informations sur l’utilisation de ce suivi par défaut. Lorsqu’il est temps de lire la vidéo, vous pouvez demander une liste des pistes audio disponibles, éventuellement permettre à l’utilisateur de sélectionner une piste et définir la lecture de la vidéo avec la piste sélectionnée.

>[!TIP]
>
>Bien que rare, si une piste audio supplémentaire devient disponible une fois que TVSDK a créé la variable `MediaPlayerItem`, TVSDK déclenche une `MediaPlayerItem.AUDIO_TRACK_UPDATED` .

## Ajout d’API {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}

Les API suivantes ont été ajoutées pour prendre en charge un son alternatif :

`hasAlternateAudio`

Si le média spécifié comporte une autre piste audio, autre que la piste par défaut, cette fonction booléenne renvoie `true`. S’il n’existe aucune autre piste audio, la fonction renvoie `false`.

```java
boolean hasAlternateAudio();
```

** `getAudioTracks`**

Cette fonction renvoie la liste de toutes les pistes audio disponibles actuelles dans un média spécifié.

```java
List<AudioTrack> getAudioTracks();
```

`getSelectedAudioTrack`

Cette fonction renvoie les autres propriétés et la piste audio actuellement sélectionnée, telles que la langue. La sélection automatique de la piste peut également être extraite.

```java
AudioTrack getSelectedAudioTrack();
```

`selectAudioTrack`

Cette fonction sélectionne une autre piste audio à lire.

```java
void selectAudioTrack(AudioTrack audioTrack);
```

Par exemple :

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
