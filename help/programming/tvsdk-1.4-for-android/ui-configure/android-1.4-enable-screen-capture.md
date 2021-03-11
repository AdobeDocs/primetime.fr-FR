---
keywords: setSecure;VideoEngineView
title: Activer la capture d’écran
description: Activer la capture d’écran
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---


# Activer la capture d’écran{#enable-screen-capture}

TVSDK n’autorise pas la capture d’écran par défaut. Le lecteur appelle `setSecure(true)` sur l&#39;objet `com.adobe.ave.VideoEngineView` au moment de la construction. Vous avez accès à cet objet, car vous devez construire un objet `VideoEngineView` et le fournir à l&#39;objet `VideoEngine`.

Pour activer la capture d’écran dans votre application :

1. Construisez l&#39;objet `com.adobe.ave.VideoEngineView`.
1. Appelez `setSecure(false)` sur votre objet `VideoEngineView`.
