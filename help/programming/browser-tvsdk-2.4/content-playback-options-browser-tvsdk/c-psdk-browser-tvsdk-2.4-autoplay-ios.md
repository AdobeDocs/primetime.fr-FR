---
description: 'null'
seo-description: 'null'
seo-title: Lecture automatique sur iOS
title: Lecture automatique sur iOS
uuid: d15bad24-be50-49e5-90f4-68dbda96fb6d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Lecture automatique sur iOS{#autoplay-on-ios}

L’implémentation de l’API de volume d’AdobePSDK.MediaPlayer permet la lecture automatique du contenu sur les périphériques exécutant iOS version 10 ou ultérieure. iOS autorise la lecture automatique uniquement lorsque le volume est coupé. Lorsque le volume est défini sur zéro, l’API définit la `muted` propriété de la balise vidéo sur `true`, sinon la `muted` propriété est définie sur `false`. L’ `play` API début la lecture sans aucune interaction de l’utilisateur ni geste de l’utilisateur.

Pour une lecture automatique sur iPhone, définissez en outre la `playsInline` propriété de la `video` balise sur `true`.

```
videoDiv.getElementsByTagName('video')[0].playsInline = true;
```

>[!NOTE]
>
>L’utilisation de `playsInline` la propriété début la lecture sans le mode plein écran.

