---
seo-title: Exemple d’une ressource VOD personnalisée
title: Exemple d’une ressource VOD personnalisée
uuid: 23ff3778-09d4-43ef-89c3-67f8fc56f5da
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
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

