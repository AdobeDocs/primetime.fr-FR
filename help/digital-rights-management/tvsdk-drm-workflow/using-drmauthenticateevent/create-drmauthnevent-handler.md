---
description: L’objet DRMAuthenticateEvent est distribué lorsqu’un objet Primetime tente de lire un contenu protégé nécessitant des informations d’identification utilisateur pour l’authentification avant la lecture (et l’authentification n’a pas encore été effectuée). Le gestionnaire DRMAuthenticateEvent est chargé de rassembler les informations d’identification requises (nom d’utilisateur, mot de passe et type) et de transmettre les valeurs à la méthode .setDRMAuthenticationCredentials() pour validation.
seo-description: L’objet DRMAuthenticateEvent est distribué lorsqu’un objet Primetime tente de lire un contenu protégé nécessitant des informations d’identification utilisateur pour l’authentification avant la lecture (et l’authentification n’a pas encore été effectuée). Le gestionnaire DRMAuthenticateEvent est chargé de rassembler les informations d’identification requises (nom d’utilisateur, mot de passe et type) et de transmettre les valeurs à la méthode .setDRMAuthenticationCredentials() pour validation.
seo-title: Création d’un gestionnaire DRMAuthenticateEvent
title: Création d’un gestionnaire DRMAuthenticateEvent
uuid: 58330691-d0b5-46bd-9b1d-8dc597580d31
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc

---


# Création d’un gestionnaire DRMAuthenticateEvent{#create-a-drmauthenticateevent-handler}

L’objet DRMAuthenticateEvent est distribué lorsqu’un objet Primetime tente de lire un contenu protégé nécessitant des informations d’identification utilisateur pour l’authentification avant la lecture (et l’authentification n’a pas encore été effectuée). Le gestionnaire DRMAuthenticateEvent est chargé de rassembler les informations d’identification requises (nom d’utilisateur, mot de passe et type) et de transmettre les valeurs à la méthode .setDRMAuthenticationCredentials() pour validation.

L’application doit fournir un mécanisme pour obtenir les informations d’identification de l’utilisateur. Par exemple, l’application peut fournir à un utilisateur une interface utilisateur simple pour saisir des valeurs de nom d’utilisateur et de mot de passe. Il doit également fournir un mécanisme de gestion et de limitation des tentatives d’échec d’authentification répétées.

Créez un gestionnaire de  qui transmet un jeu d’informations d’identification d’authentification codées en dur à l’objet Primetime à l’origine de l’ de :

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

(Le code de lecture de la vidéo et de vérification d’une connexion réussie au flux vidéo n’est pas inclus ici.)
