---
description: Une publicité peut avoir plusieurs éléments créatifs, dont un est sélectionné pour être lu.
title: Types MIME valides
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Types MIME valides{#valid-mime-types}

Une publicité peut avoir plusieurs éléments créatifs, dont un est sélectionné pour être lu.

Avec les types MIME, vous pouvez spécifier les types de création que les utilisateurs peuvent prioriser. Les types MIME spécifiés par les utilisateurs et les types MIME pris en charge par le Browser TVSDK sont utilisés pour déterminer la création qui sera prioritaire.

Pour définir les types MIME valides dans Browser TVSDK :

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var mimeTypes = [“video/mp4”, “application/x-mpegURL”]; 
auditudeSettings.validMimeTypes = mimeTypes; 
```

where `mimeTypes` est un tableau de chaînes, et chaque chaîne représente un type MIME.

Si plusieurs fichiers multimédias sont renvoyés pour une publicité, la sélection dépend de l’ordre dans lequel les fichiers multimédias apparaissent. `validMimeTypes` tableau. Les types MIME ayant un index inférieur reçoivent une préférence par rapport à ceux ayant un index supérieur.
