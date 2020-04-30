---
seo-title: Exemple d’une ressource VOD personnalisée
title: Exemple d’une ressource VOD personnalisée
uuid: 21e83b47-d7e2-4a2d-8a0b-80dd09e253a8
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Exemple d’une ressource VOD personnalisée {#example-of-a-customized-vod-asset}

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

* Une notification indiquant si `#EXT-X-ASSET` des balises, ou tout autre ensemble de noms de balises personnalisés auxquels vous vous êtes abonné, existent dans le fichier.
* Insérez des publicités lorsqu’une `#EXT-X-AD` balise, ou tout autre nom de balise personnalisé, se trouve dans le flux.

