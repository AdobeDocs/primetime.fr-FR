---
description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.
seo-description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.
seo-title: Attendre un état valide
title: Attendre un état valide
uuid: ad9df366-c443-4e6b-a7ab-658d5691eb94
translation-type: tm+mt
source-git-commit: a63768e51c911914a6ba9d884e2587fa34939f9d
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# Attendre un état {#wait-for-a-valid-state} valide

Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.

Le lecteur passe d’un état à l’autre. En attendant que le lecteur ait le bon état, vous avez la garantie que la ressource multimédia a bien été chargée. Si le lecteur n&#39;a pas au moins l&#39;état requis, de nombreuses méthodes du lecteur lancent `IllegalStateException`.

Le statut requis est généralement `PTMediaPlayerStatusReady`.