---
description: 'null'
keywords: setSecure;VideoEngineView
seo-description: 'null'
seo-title: Activer la capture d’écran
title: Activer la capture d’écran
uuid: f3d18729-e13e-47f9-b4b8-f93a2874ef16
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Activer la capture d’écran{#enable-screen-capture}

TVSDK désactive la capture d’écran par défaut. Le joueur appelle `setSecure(true)` l&#39; `com.adobe.ave.VideoEngineView` objet au moment de la construction. Vous avez accès à cet objet, car vous devez construire un `VideoEngineView` objet et le fournir à l’ `VideoEngine` objet.

Pour activer la capture d’écran dans votre application :

1. Construisez l’ `com.adobe.ave.VideoEngineView` objet.
1. Appelez `setSecure(false)` votre `VideoEngineView` objet.
