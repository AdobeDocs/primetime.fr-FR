---
description: L’indicateur forcefFlash de la liste source force le Flash de secours pour une URL. Pour cette URL, vous pouvez utiliser le Flash Player d’Adobe pour lire le contenu.
title: Obligation de la reprise du Flash à l'aide de la liste de la source du média
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 2%

---


# Obligation de la reprise du Flash à l’aide de la liste de la source du média {#forcing-the-flash-fallback-using-the-media-source-list}

L’indicateur forcefFlash de la liste source force le Flash de secours pour une URL. Pour cette URL, vous pouvez utiliser le Flash Player d’Adobe pour lire le contenu.

Dans la liste source du média (par exemple dans le fichier `sources.js`), vous pouvez définir `forceflash` sur `true`. Par exemple :

```js
{ 
        "title":"Title of the item listed in the media source list",
        "description":"Description of the item listed in the media source list",
        "isLive":true,
        "content":[ 
            { 
                "format":"HLS",
                "url":"https://path_to_HLS_stream.m3u8"
            },
 
        ],
        "forceflash" : true
},
```

