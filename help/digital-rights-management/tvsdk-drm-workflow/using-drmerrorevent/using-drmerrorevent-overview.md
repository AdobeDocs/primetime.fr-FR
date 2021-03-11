---
title: Utilisation de l’aperçu de la classe DRMErrorEvent
description: Utilisation de l’aperçu de la classe DRMErrorEvent
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---


# Utilisation de l&#39;aperçu de la classe DRMErrorEvent {#using-the-drmerrorevent-class-overview}

Primetime distribue un objet `DRMErrorEvent` lorsqu’un objet Primetime, qui tente de lire du contenu protégé, rencontre une erreur [DRM](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages) liée à la lecture du contenu protégé. Si les informations d’identification de l’utilisateur ne sont pas valides, l’objet `DRMAuthenticateEvent` est distribué à plusieurs reprises jusqu’à ce que l’utilisateur entre des informations d’identification valides ou que l’application refuse d’autres tentatives. L&#39;application est chargée d&#39;écouter tout autre événement d&#39;erreur DRM pour détecter, identifier et gérer les [erreurs DRM](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages).

Même avec des informations d’identification d’utilisateur valides, les termes de la licence du contenu peuvent toujours empêcher un utilisateur d’afficher le contenu chiffré. Par exemple, un utilisateur peut se voir refuser l’accès lorsqu’il tente de vue du contenu dans une application non autorisée (par exemple, la liste Application Allow). Une application non autorisée est une application qui n’a pas été signée avec un certificat de signature d’application autorisé. Dans ce cas, un objet `DRMErrorEvent` est distribué.

Les événements d’erreur peuvent également être déclenchés si le contenu est corrompu ou si la version de l’application ne correspond pas à ce que la licence spécifie. L&#39;application doit fournir un mécanisme approprié pour gérer les erreurs.
