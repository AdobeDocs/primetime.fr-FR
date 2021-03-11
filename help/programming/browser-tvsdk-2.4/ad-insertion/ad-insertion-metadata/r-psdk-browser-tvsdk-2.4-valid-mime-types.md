---
description: Une publicité peut comporter plusieurs éléments créatifs, dont un est sélectionné pour être lu.
title: Types MIME valides
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---


# Types mime valides{#valid-mime-types}

Une publicité peut comporter plusieurs éléments créatifs, dont un est sélectionné pour être lu.

Avec les types MIME, vous pouvez spécifier les types créatifs que les utilisateurs peuvent classer par priorité. Les types MIME spécifiés par les utilisateurs et les types MIME pris en charge par le navigateur TVSDK sont utilisés pour déterminer quel créatif sera prioritaire.

Pour définir les types MIME valides dans le navigateur TVSDK :

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var mimeTypes = [“video/mp4”, “application/x-mpegURL”]; 
auditudeSettings.validMimeTypes = mimeTypes; 
```

où `mimeTypes` est un tableau de chaînes et chaque chaîne représente un type mime.

Si plusieurs fichiers multimédias sont renvoyés pour une publicité, la sélection dépend de l&#39;ordre dans lequel les fichiers multimédias apparaissent dans la baie `validMimeTypes`. Les types mime présentant un index inférieur se voient accorder une préférence par rapport à ceux ayant un index supérieur.
