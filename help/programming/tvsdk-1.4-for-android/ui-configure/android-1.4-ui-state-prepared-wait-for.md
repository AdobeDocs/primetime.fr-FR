---
description: TVSDK vous permet de contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur.
seo-description: TVSDK vous permet de contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur.
seo-title: Attendre un état valide
title: Attendre un état valide
uuid: 22b68162-1625-4e8a-8566-b0c198155622
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Attendre un état {#wait-for-a-valid-state} valide

TVSDK vous permet de contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur.

Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.
Le joueur se déplace à travers différents états. En attendant que le lecteur soit à l’état correct, vous avez la garantie que la ressource multimédia a été chargée avec succès. Si le lecteur n&#39;est pas dans l&#39;état requis au moins, de nombreuses méthodes du lecteur lancent `IllegalStateException`.

L’état requis est généralement PRÉPARÉ.
