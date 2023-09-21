---
title: Utilisation de la classe DRMErrorEvent - Aperçu
description: Utilisation de la classe DRMErrorEvent - Aperçu
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---


# Utilisation de la classe DRMErrorEvent - Aperçu {#using-the-drmerrorevent-class-overview}

Primetime distribue une `DRMErrorEvent` lorsqu’un objet Primetime, en essayant de lire du contenu protégé, rencontre une [Erreur liée à DRM](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages). Si les informations d’identification de l’utilisateur ne sont pas valides, la variable `DRMAuthenticateEvent` distribue à plusieurs reprises jusqu’à ce que l’utilisateur saisisse des informations d’identification valides ou que l’application refuse d’autres tentatives. L’application est chargée d’écouter tout autre événement d’erreur DRM pour détecter, identifier et gérer la variable [Erreurs liées à DRM](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages).

Même avec des informations d’identification d’utilisateur valides, les termes de la licence du contenu peuvent toujours empêcher un utilisateur de voir le contenu chiffré. Par exemple, un utilisateur peut se voir refuser l’accès s’il tente d’afficher du contenu dans une application non autorisée (par exemple, une liste autorisée des applications). Une application non autorisée est une application qui n’a pas été signée avec un certificat de signature d’application autorisé. Dans ce cas, une `DRMErrorEvent` est distribué.

Les événements d’erreur peuvent également être déclenchés si le contenu est corrompu ou si la version de l’application ne correspond pas à ce que la licence spécifie. L’application doit fournir un mécanisme approprié pour gérer les erreurs.
