---
description: L’indicateur forcefFlash dans la liste source force le Flash de secours pour une URL. Pour cette URL, vous pouvez utiliser le Flash Player Adobe pour lire le contenu.
title: Forcer le Flash de secours à l’aide de la liste source du média
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# Forcer le Flash de secours à l’aide de la liste source du média{#forcing-the-flash-fallback-using-the-media-source-list}

L’indicateur forcefFlash dans la liste source force le Flash de secours pour une URL. Pour cette URL, vous pouvez utiliser le Flash Player Adobe pour lire le contenu.

Dans la liste des sources du média (par exemple, dans la fonction `sources.js` ), vous pouvez définir `forceflash` to `true`. Par exemple :

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
