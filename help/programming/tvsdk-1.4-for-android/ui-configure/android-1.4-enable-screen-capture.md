---
description: 'null'
keywords: setSecure;VideoEngineView
seo-description: 'null'
seo-title: Activer la capture d’écran
title: Activer la capture d’écran
uuid: f3d18729-e13e-47f9-b4b8-f93a2874ef16
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---


# Activer la capture d’écran{#enable-screen-capture}

TVSDK n’autorise pas la capture d’écran par défaut. Le lecteur appelle `setSecure(true)` sur l&#39;objet `com.adobe.ave.VideoEngineView` au moment de la construction. Vous avez accès à cet objet, car vous devez construire un objet `VideoEngineView` et le fournir à l&#39;objet `VideoEngine`.

Pour activer la capture d’écran dans votre application :

1. Construisez l&#39;objet `com.adobe.ave.VideoEngineView`.
1. Appelez `setSecure(false)` sur votre objet `VideoEngineView`.
