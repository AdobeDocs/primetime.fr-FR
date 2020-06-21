---
seo-title: Utilisation de l’aperçu de la classe DRMErrorEvent
title: Utilisation de l’aperçu de la classe DRMErrorEvent
uuid: cbb9c1a7-3c50-479d-b7e5-63010a696dfa
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---


# Utilisation de l’aperçu de la classe DRMErrorEvent {#using-the-drmerrorevent-class-overview}

Primetime distribue un `DRMErrorEvent` objet lorsqu’un objet Primetime, qui tente de lire du contenu protégé, rencontre une erreur [liée au](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)DRM. Si les informations d’identification de l’utilisateur ne sont pas valides, l’ `DRMAuthenticateEvent` objet est distribué à plusieurs reprises jusqu’à ce que l’utilisateur entre des informations d’identification valides ou que l’application refuse d’autres tentatives. L&#39;application est chargée d&#39;écouter tout autre événement d&#39;erreur DRM pour détecter, identifier et gérer les erreurs [liées au](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)DRM.

Même avec des informations d’identification d’utilisateur valides, les termes de la licence du contenu peuvent toujours empêcher un utilisateur d’afficher le contenu chiffré. Par exemple, un utilisateur peut se voir refuser l’accès lorsqu’il tente de vue du contenu dans une application non autorisée (par exemple, la liste Application Allow). Une application non autorisée est une application qui n’a pas été signée avec un certificat de signature d’application autorisé. Dans ce cas, un `DRMErrorEvent` objet est distribué.

Les événements d’erreur peuvent également être déclenchés si le contenu est corrompu ou si la version de l’application ne correspond pas à ce que la licence spécifie. L&#39;application doit fournir un mécanisme approprié pour gérer les erreurs.
