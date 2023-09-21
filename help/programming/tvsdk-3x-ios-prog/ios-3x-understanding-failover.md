---
description: La gestion du basculement se produit lorsqu’une liste de lecture de variante comporte plusieurs rendus pour le même débit, et que l’un des rendus cesse de fonctionner. TVSDK bascule entre les rendus.
title: Basculement
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Basculement {#failover}

La gestion du basculement se produit lorsqu’une liste de lecture de variante comporte plusieurs rendus pour le même débit, et que l’un des rendus cesse de fonctionner. TVSDK bascule entre les rendus.

L&#39;exemple suivant montre une liste de lecture de variante avec des URL de basculement d&#39;un même débit :

```
#EXTM3U
#EXT-X-STREAM-INF:PROGRAM-ID=1, BANDWIDTH =700000
https://sj2slu225.corp.adobe.com:8090/_default_/_default_/livestream.m3u8   

#EXT-X-STREAM-INF:PROGRAM-ID=1, BANDWIDTH =700000
https://sj2slu225.corp.adobe.com:8091/_default_/_default_/livestream.m3u8
```

Lorsque TVSDK charge la liste de lecture des variantes, il crée une file d’attente contenant les URL de tous les rendus du contenu pour le même débit binaire. Lorsqu’une demande d’URL échoue, TVSDK utilise l’URL suivante du même débit depuis la file d’attente de basculement. À tout moment d’échec spécifique, TVSDK parcourt toutes les URL disponibles jusqu’à ce qu’il en trouve une qui fonctionne correctement ou jusqu’à ce qu’il ait tenté toutes les URL disponibles. Si TVSDK a tenté d’atteindre toutes les URL disponibles et qu’aucune URL ne fonctionne, TVSDK cesse de tenter de lire le contenu.

Le basculement se produit uniquement au niveau M3U8, ce qui signifie :

* Pour VOD, le basculement ne peut avoir lieu que lorsqu’il commence à essayer de jouer et non après le début de la lecture.
* Pour la diffusion en continu en direct, le basculement peut se produire au milieu de la diffusion.

>[!TIP]
>
>TVSDK, plutôt que le lecteur Apple AV Foundation, permet la gestion du basculement.
