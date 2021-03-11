---
description: TVSDK vous permet de contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur.
title: Attendre un état valide
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Attendre un état {#wait-for-a-valid-state} valide

TVSDK vous permet de contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur.

Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.
Le joueur se déplace à travers différents états. En attendant que le lecteur soit à l’état correct, vous avez la garantie que la ressource multimédia a été chargée avec succès. Si le lecteur n&#39;est pas dans l&#39;état requis au moins, de nombreuses méthodes du lecteur lancent `IllegalStateException`.

L’état requis est généralement PRÉPARÉ.
