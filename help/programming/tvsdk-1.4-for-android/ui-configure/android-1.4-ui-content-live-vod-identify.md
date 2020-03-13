---
description: Dans certains cas, vous devez savoir si le contenu multimédia est en direct ou VOD.
seo-description: Dans certains cas, vous devez savoir si le contenu multimédia est en direct ou VOD.
seo-title: Déterminer si le contenu est actif ou VOD
title: Déterminer si le contenu est actif ou VOD
uuid: cd71b8d3-259a-48f8-a6ad-02b57da146a7
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Déterminer si le contenu est actif ou VOD{#identify-whether-the-content-is-live-or-vod}

Dans certains cas, vous devez savoir si le contenu multimédia est en direct ou VOD.

1. Assurez-vous que le lecteur est au moins à l’état PRÉPARÉ.
1. Déterminez si le `MediaPlayerItem` contenu est en direct (true) ou VOD (false).

   ```java
   boolean isLive();
   ```

