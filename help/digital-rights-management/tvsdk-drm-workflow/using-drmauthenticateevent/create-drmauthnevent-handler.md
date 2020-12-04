---
description: L’objet DRMAuthenticateEvent est distribué lorsqu’un objet Primetime tente de lire du contenu protégé qui nécessite des informations d’identification utilisateur pour l’authentification avant la lecture (et l’authentification n’a pas encore été effectuée). Le gestionnaire DRMAuthenticateEvent est chargé de rassembler les informations d’identification requises (nom d’utilisateur, mot de passe et type) et de transmettre les valeurs à la méthode .setDRMAuthenticationCredentials() pour validation.
seo-description: L’objet DRMAuthenticateEvent est distribué lorsqu’un objet Primetime tente de lire du contenu protégé qui nécessite des informations d’identification utilisateur pour l’authentification avant la lecture (et l’authentification n’a pas encore été effectuée). Le gestionnaire DRMAuthenticateEvent est chargé de rassembler les informations d’identification requises (nom d’utilisateur, mot de passe et type) et de transmettre les valeurs à la méthode .setDRMAuthenticationCredentials() pour validation.
seo-title: Création d’un gestionnaire DRMAuthenticateEvent
title: Création d’un gestionnaire DRMAuthenticateEvent
uuid: 58330691-d0b5-46bd-9b1d-8dc597580d31
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# Création d’un gestionnaire DRMAuthenticateEvent{#create-a-drmauthenticateevent-handler}

L’objet DRMAuthenticateEvent est distribué lorsqu’un objet Primetime tente de lire du contenu protégé qui nécessite des informations d’identification utilisateur pour l’authentification avant la lecture (et l’authentification n’a pas encore été effectuée). Le gestionnaire DRMAuthenticateEvent est chargé de rassembler les informations d’identification requises (nom d’utilisateur, mot de passe et type) et de transmettre les valeurs à la méthode .setDRMAuthenticationCredentials() pour validation.

L’application doit fournir un mécanisme pour obtenir les informations d’identification de l’utilisateur. Par exemple, l’application peut fournir à un utilisateur une interface utilisateur simple pour entrer des valeurs de nom d’utilisateur et de mot de passe. En outre, il doit fournir un mécanisme de gestion et de limitation des tentatives d&#39;authentification répétées en cas d&#39;échec.

Créez un gestionnaire de événements qui transmet un ensemble d’informations d’identification d’authentification codées en dur à l’objet Primetime à l’origine du événement :

```
var connection:NetConnection = new NetConnection();  
connection.connect(null);  
var videoStream:Primetime = new Primetime(connection);  
 
videoStream.addEventListener( 
  DRMAuthenticateEvent.DRM_AUTHENTICATE,  
  drmAuthenticateEventHandler)  
  private function drmAuthenticateEventHandler(event:DRMAuthenticateEvent):void {  
    videoStream.setDRMAuthenticationCredentials("administrator", "password", "drm");  
} 
```

(Le code permettant de lire la vidéo et de s’assurer qu’une connexion réussie au flux vidéo a été établie n’est pas inclus ici.)
