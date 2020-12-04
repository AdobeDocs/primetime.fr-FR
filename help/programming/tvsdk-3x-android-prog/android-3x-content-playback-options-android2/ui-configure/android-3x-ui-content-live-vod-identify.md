---
description: Vous devrez peut-être savoir si le contenu multimédia est en direct ou sur demande (VOD).
seo-description: Vous devrez peut-être savoir si le contenu multimédia est en direct ou sur demande (VOD).
seo-title: Déterminer si le contenu est actif ou VOD
title: Déterminer si le contenu est actif ou VOD
uuid: e6a66104-97fb-438a-8356-e21f94058c85
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# Déterminer si le contenu est actif ou VOD {#identify-whether-the-content-is-live-or-vod}

Vous devrez peut-être savoir si le contenu multimédia est en direct ou sur demande (VOD).

1. Assurez-vous que le lecteur est à au moins l’état `PREPARED`.
1. Déterminez si le contenu `MediaPlayerItem` est actif ( `true`) ou VOD ( `false`).

   ```java
   boolean isLive();
   ```
