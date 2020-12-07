---
description: 'null'
seo-description: 'null'
seo-title: Lecture automatique sur iOS
title: Lecture automatique sur iOS
uuid: d15bad24-be50-49e5-90f4-68dbda96fb6d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# Lecture automatique sur iOS{#autoplay-on-ios}

L’implémentation de l’API de volume d’AdobePSDK.MediaPlayer permet la lecture automatique du contenu sur les périphériques exécutant iOS version 10 ou ultérieure. iOS autorise la lecture automatique uniquement lorsque le volume est coupé. Lorsque le volume est défini sur zéro, l’API définit la propriété `muted` de la balise vidéo sur `true`, sinon la propriété `muted` est définie sur `false`. L’API `play` début la lecture sans aucune interaction de l’utilisateur ni geste de l’utilisateur.

Pour la lecture automatique sur iPhone, définissez en outre la propriété `playsInline` de la balise `video` sur `true`.

```
videoDiv.getElementsByTagName('video')[0].playsInline = true;
```

>[!NOTE]
>
>L’utilisation de la propriété `playsInline` début la lecture sans le mode plein écran.

