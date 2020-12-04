---
description: L’indicateur forcefFlash de la liste source force le Flash de secours pour une URL. Pour cette URL, vous pouvez utiliser le Flash Player d’Adobe pour lire le contenu.
seo-description: L’indicateur forcefFlash de la liste source force le Flash de secours pour une URL. Pour cette URL, vous pouvez utiliser le Flash Player d’Adobe pour lire le contenu.
seo-title: Obligation de la reprise du Flash à l'aide de la liste de la source du média
title: Obligation de la reprise du Flash à l'aide de la liste de la source du média
uuid: 04b09734-15f7-4e7e-8802-344f550f9b05
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

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

