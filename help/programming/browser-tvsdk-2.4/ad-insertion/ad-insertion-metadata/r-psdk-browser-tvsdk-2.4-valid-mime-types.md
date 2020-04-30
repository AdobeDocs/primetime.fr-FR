---
description: Une publicité peut comporter plusieurs éléments créatifs, dont un est sélectionné pour être lu.
seo-description: Une publicité peut comporter plusieurs éléments créatifs, dont un est sélectionné pour être lu.
seo-title: Types MIME valides
title: Types MIME valides
uuid: ab2baac9-a9ef-44f1-83a1-2e6e471e3231
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Types MIME valides{#valid-mime-types}

Une publicité peut comporter plusieurs éléments créatifs, dont un est sélectionné pour être lu.

Avec les types MIME, vous pouvez spécifier les types créatifs que les utilisateurs peuvent classer par priorité. Les types MIME spécifiés par les utilisateurs et les types MIME pris en charge par le navigateur TVSDK sont utilisés pour déterminer quel créatif sera prioritaire.

Pour définir les types MIME valides dans le navigateur TVSDK :

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var mimeTypes = [“video/mp4”, “application/x-mpegURL”]; 
auditudeSettings.validMimeTypes = mimeTypes; 
```

où `mimeTypes` est un tableau de chaînes, et chaque chaîne représente un type mime.

Si plusieurs fichiers multimédias sont renvoyés pour une publicité, la sélection dépend de l&#39;ordre dans lequel les fichiers multimédias apparaissent dans le `validMimeTypes` tableau. Les types mime présentant un index inférieur se voient accorder une préférence par rapport à ceux ayant un index supérieur.
