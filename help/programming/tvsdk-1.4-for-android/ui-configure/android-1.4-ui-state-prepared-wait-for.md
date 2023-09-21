---
description: TVSDK permet de contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur.
title: Attente d’un état valide
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Attente d’un état valide {#wait-for-a-valid-state}

TVSDK permet de contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur.

Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.
Le lecteur se déplace à travers différents états. En attendant que le lecteur se trouve dans l’état correct, vérifiez que la ressource multimédia a bien été chargée. Si le lecteur n’est pas dans l’état requis au moins, de nombreuses méthodes du lecteur sont lancées `IllegalStateException`.

L’état requis est généralement PRÉPARÉ.
