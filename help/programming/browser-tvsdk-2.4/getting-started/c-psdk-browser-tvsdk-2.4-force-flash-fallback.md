---
description: L’indicateur forcefflash dans l’source  force le renvoi Flash pour une URL. Pour cette URL, vous pouvez utiliser Adobe Flash Player pour lire le contenu.
seo-description: L’indicateur forcefflash dans l’source  force le renvoi Flash pour une URL. Pour cette URL, vous pouvez utiliser Adobe Flash Player pour lire le contenu.
seo-title: 'Forcer la reprise Flash à l''aide du de source multimédia '
title: 'Forcer la reprise Flash à l''aide du de source multimédia '
uuid: 04b09734-15f7-4e7e-8802-344f550f9b05
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Forcer la reprise Flash à l&#39;aide du de source multimédia{#forcing-the-flash-fallback-using-the-media-source-list}

L’indicateur forcefflash dans l’source  force le renvoi Flash pour une URL. Pour cette URL, vous pouvez utiliser Adobe Flash Player pour lire le contenu.

Dans le  de source du média (par exemple dans le `sources.js` fichier), vous pouvez définir `forceflash` sur `true`. Par exemple :

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

