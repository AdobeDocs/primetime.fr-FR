---
description: La gestion du basculement se produit lorsqu’une variante de liste de lecture comporte plusieurs rendus pour le même débit et que l’un des rendus ne fonctionne plus. TVSDK bascule entre les rendus.
seo-description: La gestion du basculement se produit lorsqu’une variante de liste de lecture comporte plusieurs rendus pour le même débit et que l’un des rendus ne fonctionne plus. TVSDK bascule entre les rendus.
seo-title: Basculement
title: Basculement
uuid: 064886ab-afa2-4afc-b795-d094b31934b8
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---


# Basculement {#failover}

La gestion du basculement se produit lorsqu’une variante de liste de lecture comporte plusieurs rendus pour le même débit et que l’un des rendus ne fonctionne plus. TVSDK bascule entre les rendus.

L’exemple suivant montre une variante de liste de lecture avec des URL de basculement du même débit :

```
#EXTM3U
#EXT-X-STREAM-INF:PROGRAM-ID=1, BANDWIDTH =700000
https://sj2slu225.corp.adobe.com:8090/_default_/_default_/livestream.m3u8   

#EXT-X-STREAM-INF:PROGRAM-ID=1, BANDWIDTH =700000
https://sj2slu225.corp.adobe.com:8091/_default_/_default_/livestream.m3u8
```

Lorsque TVSDK charge la liste de lecture des variantes, il crée une file d’attente contenant les URL de tous les rendus du contenu pour le même débit de bits. En cas d’échec d’une demande d’URL, TVSDK utilise l’URL suivante du même débit depuis la file d’attente de basculement. En cas de défaillance spécifique, TVSDK parcourt toutes les URL disponibles une fois jusqu’à ce qu’il en trouve une qui fonctionne correctement ou jusqu’à ce qu’il ait tenté toutes les URL disponibles. Si TVSDK a essayé de lire toutes les URL disponibles et qu’aucune URL ne fonctionne, TVSDK arrête de lire le contenu.

Le basculement se produit uniquement au niveau M3U8, ce qui signifie :

* Pour VOD, le basculement ne peut se produire que lorsqu’il commence à essayer de jouer et non après le début de la lecture.
* Pour la diffusion en continu en direct, le basculement peut se produire au milieu du flux.

>[!TIP]
>
>TVSDK, plutôt que le lecteur Apple AV Foundation, permet la gestion du basculement.