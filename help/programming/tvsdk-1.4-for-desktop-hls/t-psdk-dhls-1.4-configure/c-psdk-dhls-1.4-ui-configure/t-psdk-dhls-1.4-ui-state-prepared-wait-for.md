---
description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit disposer d’un état valide.
title: Attente d’un état valide
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Attente d’un état valide {#wait-for-a-valid-state}

TVSDK permet de contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur. Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être en état valide.

Le lecteur passe en revue différents états. En attendant que le lecteur soit dans le bon état, vous avez la garantie que la ressource multimédia a bien été chargée. Si le lecteur n’est pas au moins dans l’état requis, de nombreuses méthodes du lecteur lancent `IllegalStateException`.

L’état requis est généralement PRÉPARÉ.

1. Pour confirmer que l’état est PRÉPARÉ :

   Lorsque le lecteur est en cours d’initialisation, attendez que TVSDK appelle le rappel pour la variable `MediaPlayerStatusChangeEvent.STATUS_CHANGED` avec l’état PREPARED .

   Pour vérifier si l’état actuel de la variable `MediaPlayer` est au moins PRÊT.

   ```
   function getstatus():String;
   ```
