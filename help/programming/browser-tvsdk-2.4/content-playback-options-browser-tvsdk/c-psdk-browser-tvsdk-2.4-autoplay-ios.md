---
title: Lecture automatique sur iOS
description: Lecture automatique sur iOS
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# Lecture automatique sur iOS{#autoplay-on-ios}

La mise en oeuvre de l’API de volume d’AdobePSDK.MediaPlayer permet la lecture automatique du contenu sur les appareils exécutant iOS version 10 ou ultérieure. iOS autorise la lecture automatique uniquement lorsque le volume est en mode muet. Lorsque le volume est défini sur zéro, l’API définit la variable `muted` de la balise vidéo à `true`, sinon la variable `muted` est définie sur `false`. La variable `play` L’API lance la lecture sans intervention de l’utilisateur ni geste de l’utilisateur.

Pour une lecture automatique sur iPhone, définissez également la variable `playsInline` de la propriété `video` de `true`.

```
videoDiv.getElementsByTagName('video')[0].playsInline = true;
```

>[!NOTE]
>
>Utilisation de `playsInline` permet de lancer la lecture sans passer par le mode plein écran.
