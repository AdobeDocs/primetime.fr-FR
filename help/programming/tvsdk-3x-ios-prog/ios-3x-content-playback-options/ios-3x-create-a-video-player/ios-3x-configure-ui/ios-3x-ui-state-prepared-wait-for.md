---
description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit avoir un état valide.
seo-description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit avoir un état valide.
seo-title: Attendre un état valide
title: Attendre un état valide
uuid: ad9df366-c443-4e6b-a7ab-658d5691eb94
translation-type: tm+mt
source-git-commit: a63768e51c911914a6ba9d884e2587fa34939f9d

---


# Attendre un état valide {#wait-for-a-valid-state}

Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit avoir un état valide.

Le joueur passe d’un état à l’autre. En attendant que le lecteur soit dans le bon état, vous assurez que la ressource multimédia a bien été chargée. Si le lecteur n’est pas au moins dans l’état requis, de nombreuses méthodes du lecteur sont renvoyées `IllegalStateException`.

Le statut requis est généralement `PTMediaPlayerStatusReady`.