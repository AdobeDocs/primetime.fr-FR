---
seo-title: Utilisation de l’aperçu de la classe DRMErrorEvent
title: Utilisation de l’aperçu de la classe DRMErrorEvent
uuid: cbb9c1a7-3c50-479d-b7e5-63010a696dfa
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Utilisation de la classe DRMErrorEvent {#using-the-drmerrorevent-class}

Primetime distribue un `DRMErrorEvent` objet lorsqu’un objet Primetime, qui tente de lire du contenu protégé, rencontre une erreur [liée au](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)DRM. Si les informations d’identification de l’utilisateur ne sont pas valides, l’ `DRMAuthenticateEvent` objet est distribué à plusieurs reprises jusqu’à ce que l’utilisateur entre des informations d’identification valides ou que l’application refuse d’autres tentatives. L&#39;application est chargée d&#39;écouter tout autre événement d&#39;erreur DRM pour détecter, identifier et gérer les erreurs [liées au](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)DRM.

Même avec des informations d’identification d’utilisateur valides, les termes de la licence du contenu peuvent toujours empêcher un utilisateur d’afficher le contenu chiffré. Par exemple, un utilisateur peut se voir refuser l’accès pour tenter de vue du contenu dans une application non autorisée (par exemple, liste blanche des applications). Une application non autorisée est une application qui n’a pas été signée avec un certificat de signature d’application figurant sur la liste blanche. Dans ce cas, un `DRMErrorEvent` objet est distribué.

Les événements d’erreur peuvent également être déclenchés si le contenu est corrompu ou si la version de l’application ne correspond pas à ce que la licence spécifie. L&#39;application doit fournir un mécanisme approprié pour gérer les erreurs.

## Création d’un gestionnaire DRMErrorEvent {#create-a-drmerrorevent-handler}

Créez un gestionnaire de événements pour traiter les événements d’erreur envoyés à partir de Primetime lorsqu’il rencontre une erreur lors de la tentative de lecture d’un contenu protégé.

Normalement, lorsqu’une application rencontre une erreur, elle effectue un nombre indéfini de tâches de nettoyage. Il informe ensuite l’utilisateur de l’erreur et fournit des options pour résoudre le problème.

```
private function drmErrorEventHandler(event:DRMErrorEvent):void {  
    trace(event.toString());  
} 
```
