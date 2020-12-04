---
seo-title: Exemple d’une ressource VOD personnalisée
title: Exemple d’une ressource VOD personnalisée
uuid: 21e83b47-d7e2-4a2d-8a0b-80dd09e253a8
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---


# Exemple d&#39;une ressource VOD personnalisée {#example-of-a-customized-vod-asset}

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

* Une notification indiquant si des balises `#EXT-X-ASSET`, ou tout autre ensemble de noms de balises personnalisés auquel vous vous êtes abonné, existent dans le fichier.
* Insérez des publicités lorsqu’une balise `#EXT-X-AD` ou tout autre nom de balise personnalisé se trouve dans le flux.

