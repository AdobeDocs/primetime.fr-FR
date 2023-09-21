---
description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit disposer d’un état valide.
title: Attente d’un état valide
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# Attente d’un état valide {#wait-for-a-valid-state}

Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit disposer d’un état valide.

Le lecteur passe en revue différents états. En attendant que le lecteur soit dans le bon état, vous avez la garantie que la ressource multimédia a bien été chargée. Si le lecteur n’est pas au moins dans l’état requis, de nombreuses méthodes du lecteur sont lancées `IllegalStateException`.

L’état requis est généralement `PTMediaPlayerStatusReady`.
