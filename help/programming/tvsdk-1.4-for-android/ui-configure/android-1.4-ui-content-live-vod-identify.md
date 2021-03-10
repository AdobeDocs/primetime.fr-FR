---
description: Dans certains cas, vous devez savoir si le contenu multimédia est actif ou VOD.
title: Déterminer si le contenu est actif ou VOD
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---


# Déterminer si le contenu est actif ou VOD{#identify-whether-the-content-is-live-or-vod}

Dans certains cas, vous devez savoir si le contenu multimédia est actif ou VOD.

1. Assurez-vous que le lecteur est à au moins l’état PRÉPARÉ.
1. Déterminez si le contenu `MediaPlayerItem` est actif (true) ou VOD (false).

   ```java
   boolean isLive();
   ```

