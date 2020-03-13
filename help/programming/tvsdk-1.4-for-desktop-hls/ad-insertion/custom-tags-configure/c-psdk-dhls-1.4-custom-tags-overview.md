---
seo-title: Exemple d’une ressource VOD personnalisée
title: Exemple d’une ressource VOD personnalisée
uuid: 599054c3-d6ef-4f85-9a0f-39c7e4f6ab24
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Exemple d’une ressource VOD personnalisée{#example-of-a-customized-vod-asset}

Voici un exemple de ressource VOD personnalisée :

```
#EXTM3U
#EXT-X-VERSION:3
#EXT-X-TARGETDURATION:7
 
#EXT-X-ASSET:AID=10
 
#EXTINF:9.9766,
seg1.ts
 
#EXTINF:9.9766,
seg2.ts
 
#EXTINF:9.9766,
seg3.ts
 
#EXT-X-AD:DURATION=10
#EXTINF:9.9766,
seg4.ts
 
#EXTINF:9.9766,
seg5.ts
 
#EXT-X-ENDLIST
```

Votre application peut configurer les scénarios suivants :

* Une notification lorsque `#EXT-X-ASSET` des balises, ou tout autre jeu de noms de balises personnalisées auquel vous vous êtes abonné, existent dans le fichier.
* Insérez des publicités lorsqu’une `#EXT-X-AD` balise, ou tout autre nom de balise personnalisé, se trouve dans le flux.

