---
description: Dans certains cas, vous devez savoir si le contenu multimédia est actif ou VOD.
title: Déterminer si le contenu est actif ou VOD
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Déterminer si le contenu est actif ou VOD{#identify-whether-the-content-is-live-or-vod}

Dans certains cas, vous devez savoir si le contenu multimédia est actif ou VOD.

1. Assurez-vous que le lecteur est à au moins l’état PRÉPARÉ .
1. Déterminez si la variable `MediaPlayerItem` le contenu est actif (true) ou VOD (false).

   ```java
   boolean isLive();
   ```
