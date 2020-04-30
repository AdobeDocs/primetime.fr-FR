---
description: La liste de lecture d’une vidéo peut spécifier un nombre illimité de pistes audio alternatives pour le contenu vidéo principal. Par exemple, vous pouvez souhaiter ajouter différentes langues à votre contenu vidéo ou permettre à l’utilisateur de passer d’une piste à l’autre sur son périphérique pendant la lecture du contenu.
seo-description: La liste de lecture d’une vidéo peut spécifier un nombre illimité de pistes audio alternatives pour le contenu vidéo principal. Par exemple, vous pouvez souhaiter ajouter différentes langues à votre contenu vidéo ou permettre à l’utilisateur de passer d’une piste à l’autre sur son périphérique pendant la lecture du contenu.
seo-title: Autres pistes audio de la liste de lecture
title: Autres pistes audio de la liste de lecture
uuid: 47289392-ae4e-44b9-8d54-6ccee8fe1446
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Autres pistes audio de la liste de lecture {#alternate-audio-tracks-in-the-playlist}

La liste de lecture d’une vidéo peut spécifier un nombre illimité de pistes audio alternatives pour le contenu vidéo principal. Par exemple, vous pouvez souhaiter ajouter différentes langues à votre contenu vidéo ou permettre à l’utilisateur de passer d’une piste à l’autre sur son périphérique pendant la lecture du contenu.

Les autres pistes audio permettent aux utilisateurs de basculer entre plusieurs pistes de langue pour les flux vidéo HTTP (direct/linéaire et VOD) et vous n’avez pas à modifier, duplicata ou recompresser la vidéo pour chaque piste audio. Vous pouvez fournir plusieurs pistes de langue pour une ressource vidéo avant ou après le conditionnement initial de la ressource.

>[!IMPORTANT]
>
>Pour que l’audio alternatif soit mélangé à la piste vidéo du média principal, les horodatages de la piste alternative doivent correspondre aux horodatages de l’audio dans la piste principale.

La piste audio principale est incluse dans la collection de pistes audio avec le `default` libellé. Les métadonnées des autres flux audio sont incluses dans la liste de lecture dans les `#EXT-X-MEDIA` balises contenant `TYPE=AUDIO`.

Par exemple, un manifeste M3U8 spécifiant plusieurs flux audio alternatifs peut ressembler à ceci :

```
#EXTM3U
#EXT-X-MEDIA:TYPE=AUDIO,GROUP-ID="bipbop_audio",LANGUAGE="eng",NAME="BipBop Audio 1",
 AUTOSELECT=YES,DEFAULT=YES
#EXT-X-MEDIA:TYPE=AUDIO,GROUP-ID="bipbop_audio",LANGUAGE="eng",NAME="BipBop Audio 2",
 AUTOSELECT=NO,DEFAULT=NO,URI="alternate_audio_aac/prog_index.m3u8"
#EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="English",AUTOSELECT=YES,FORCED=NO,
 LANGUAGE="eng",URI="subtitles/eng/prog_index.m3u8"
#EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="English (Forced)",DEFAULT=YES,
 AUTOSELECT=YES,FORCED=YES,LANGUAGE="eng",URI="subtitles/eng_forced/prog_index.m3u8"
#EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="Français",AUTOSELECT=YES,FORCED=NO,
 LANGUAGE="fra",URI="subtitles/fra/prog_index.m3u8"
#EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=263851,CODECS="mp4a.40.2, avc1.4d400d",
 RESOLUTION=416x234,AUDIO="bipbop_audio",SUBTITLES="subs" 
gear1/prog_index.m3u8
#EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=577610,CODECS="mp4a.40.2, avc1.4d401e",
 RESOLUTION=640x360,AUDIO="bipbop_audio",SUBTITLES="subs"
gear2/prog_index.m3u8
...
```

