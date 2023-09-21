---
description: Vous devrez peut-être savoir si le contenu multimédia est en direct ou vidéo à la demande (VOD).
title: Déterminer si le contenu est actif ou VOD
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Déterminer si le contenu est actif ou VOD {#identify-whether-the-content-is-live-or-vod}

Vous devrez peut-être savoir si le contenu multimédia est en direct ou vidéo à la demande (VOD).

1. Assurez-vous que le lecteur se trouve au moins dans la variable `PREPARED` état.
1. Déterminez si la variable `MediaPlayerItem` le contenu est actif ( `true`) ou VOD ( `false`).

   ```java
   boolean isLive();
   ```
