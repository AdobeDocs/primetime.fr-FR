---
description: L’objet DRMAuthenticateEvent est distribué lorsqu’un objet Primetime tente de lire un contenu protégé qui nécessite des informations d’identification utilisateur pour l’authentification avant la lecture (et l’authentification n’a pas encore été effectuée). Le gestionnaire DRMAuthenticateEvent est chargé de rassembler les informations d’identification requises (nom d’utilisateur, mot de passe et type) et de transmettre les valeurs à la méthode .setDRMAuthenticationCredentials() pour validation.
title: Création d’un gestionnaire DRMAuthenticateEvent
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Création d’un gestionnaire DRMAuthenticateEvent{#create-a-drmauthenticateevent-handler}

L’objet DRMAuthenticateEvent est distribué lorsqu’un objet Primetime tente de lire un contenu protégé qui nécessite des informations d’identification utilisateur pour l’authentification avant la lecture (et l’authentification n’a pas encore été effectuée). Le gestionnaire DRMAuthenticateEvent est chargé de rassembler les informations d’identification requises (nom d’utilisateur, mot de passe et type) et de transmettre les valeurs à la méthode .setDRMAuthenticationCredentials() pour validation.

L’application doit fournir un mécanisme pour obtenir les informations d’identification de l’utilisateur. Par exemple, l’application peut fournir à un utilisateur une interface utilisateur simple pour saisir les valeurs de nom d’utilisateur et de mot de passe. En outre, il doit fournir un mécanisme pour gérer et limiter les tentatives d’authentification répétées en échec.

Créez un gestionnaire d’événements qui transmet un ensemble d’informations d’authentification codées en dur à l’objet Primetime à l’origine de l’événement :

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
