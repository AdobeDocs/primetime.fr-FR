---
description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.
seo-description: Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.
seo-title: Attendre un état valide
title: Attendre un état valide
uuid: 918ab021-3685-424a-b84e-683da0357724
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# Attendre un état valide {#wait-for-a-valid-state}

TVSDK vous permet de contrôler l’expérience de lecture de base pour les vidéos en direct et à la demande (VOD). TVSDK fournit des méthodes et des propriétés sur l’instance du lecteur que vous pouvez utiliser pour configurer l’interface utilisateur du lecteur. Avant de pouvoir utiliser la plupart des méthodes du lecteur TVSDK, le lecteur doit être dans un état valide.

Le lecteur passe d’un état à l’autre. En attendant que le lecteur ait le bon état, vous assurez que la ressource multimédia a été chargée avec succès. Si le lecteur n&#39;est pas au moins dans l&#39;état requis, de nombreuses méthodes du lecteur lancent jet `IllegalStateException`.

L’état requis est généralement PRÉPARÉ.

1. Pour confirmer que l’état est PRÉPARÉ :

   Lorsque le lecteur est en cours d’initialisation, attendez que TVSDK appelle le rappel pour le `MediaPlayerStatusChangeEvent.STATUS_CHANGED` événement avec l’état PRÉPARÉ.

   Pour vérifier si l’état actuel de l’ `MediaPlayer` objet est au moins PRÉPARÉ.

   ```
   function getstatus():String;
   ```
