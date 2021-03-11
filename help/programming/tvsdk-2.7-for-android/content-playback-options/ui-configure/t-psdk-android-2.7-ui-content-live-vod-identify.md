---
description: Vous devrez peut-être savoir si le contenu multimédia est en direct ou sur demande (VOD).
title: Déterminer si le contenu est actif ou VOD
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 0%

---


# Déterminer si le contenu est actif ou VOD {#identify-whether-the-content-is-live-or-vod}

Vous devrez peut-être savoir si le contenu multimédia est en direct ou sur demande (VOD).

1. Assurez-vous que le lecteur est à au moins l’état `PREPARED`.
1. Déterminez si le contenu `MediaPlayerItem` est actif ( `true`) ou VOD ( `false`).

   ```java
   boolean isLive();
   ```
