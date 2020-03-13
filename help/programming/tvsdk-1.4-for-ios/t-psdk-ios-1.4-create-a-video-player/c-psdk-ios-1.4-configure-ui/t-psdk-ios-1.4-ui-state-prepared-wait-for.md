---
description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit avoir un état valide.
seo-description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit avoir un état valide.
seo-title: Attendre un état valide
title: Attendre un état valide
uuid: e13201d7-b217-4d01-bdb7-a71855e3500e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Attendre un état valide{#wait-for-a-valid-state}

Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit avoir un état valide.

Le joueur passe d’un état à l’autre. En attendant que le lecteur soit dans le bon état, vous assurez que la ressource multimédia a bien été chargée. Si le lecteur n’est pas au moins dans l’état requis, de nombreuses méthodes du lecteur sont renvoyées `IllegalStateException`.

Le statut requis est généralement `PTMediaPlayerStatusReady`.
