---
description: Avec TVSDK, vous pouvez contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur.
seo-description: Avec TVSDK, vous pouvez contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur.
seo-title: Attendre un état valide
title: Attendre un état valide
uuid: 22b68162-1625-4e8a-8566-b0c198155622
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Attendre un état valide {#wait-for-a-valid-state}

Avec TVSDK, vous pouvez contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur.

Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.
Le joueur se déplace à travers différents états. En attendant que le lecteur soit dans l’état correct, vous assurez que la ressource multimédia a bien été chargée. Si le lecteur n’est pas dans l’état requis au moins, de nombreuses méthodes du lecteur sont lancées `IllegalStateException`.

L’état requis est généralement PRÉPARÉ.
