---
description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.
title: Attendre un état valide
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# Attendre un état {#wait-for-a-valid-state} valide

Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.

Le lecteur passe d’un état à l’autre. En attendant que le lecteur ait le bon état, vous assurez que la ressource multimédia a été chargée avec succès. Si le lecteur n&#39;a pas au moins l&#39;état requis, de nombreuses méthodes du lecteur lancent `IllegalStateException`.

Le statut requis est généralement `PTMediaPlayerStatusReady`.