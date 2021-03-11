---
title: Lecture automatique sur iOS
description: Lecture automatique sur iOS
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '93'
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

