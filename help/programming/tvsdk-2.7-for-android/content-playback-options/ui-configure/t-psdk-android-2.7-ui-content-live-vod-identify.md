---
description: Vous devrez peut-être savoir si le contenu multimédia est en direct ou sur demande (VOD).
seo-description: Vous devrez peut-être savoir si le contenu multimédia est en direct ou sur demande (VOD).
seo-title: Déterminer si le contenu est actif ou VOD
title: Déterminer si le contenu est actif ou VOD
uuid: d49315ee-8cec-4b79-adbd-a49c2a527424
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Déterminer si le contenu est actif ou VOD {#identify-whether-the-content-is-live-or-vod}

Vous devrez peut-être savoir si le contenu multimédia est en direct ou sur demande (VOD).

1. Assurez-vous que le lecteur est au moins dans l’ `PREPARED` état.
1. Déterminez si le `MediaPlayerItem` contenu est en direct ( `true`) ou VOD ( `false`).

   ```java
   boolean isLive();
   ```
