---
keywords: setSecure;VideoEngineView
title: Activer la capture d’écran
description: Activer la capture d’écran
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---

# Activer la capture d’écran{#enable-screen-capture}

TVSDK désactive la capture d’écran par défaut. Les appels du lecteur `setSecure(true)` sur le `com.adobe.ave.VideoEngineView` au moment de la construction. Vous avez accès à cet objet, car vous devez construire une `VideoEngineView` et fournissez-le à l’objet `VideoEngine` .

Pour activer la capture d’écran dans votre application :

1. Construire le `com.adobe.ave.VideoEngineView` .
1. Appeler `setSecure(false)` sur votre `VideoEngineView` .
