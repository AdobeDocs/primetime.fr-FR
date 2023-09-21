---
description: Dans certains cas, vous pouvez empêcher les utilisateurs finaux de lire du contenu sur plusieurs appareils lorsque le contenu est acheté ou loué. Si le client utilise Expressplay, vous pouvez le faire à l’aide des API Expressplay pour lier le jeton Expressplay de l’utilisateur à la machine de l’utilisateur.
title: Liaison de périphérique
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Liaison de périphérique{#device-binding}

Dans certains cas, vous pouvez empêcher les utilisateurs finaux de lire du contenu sur plusieurs appareils lorsque le contenu est acheté ou loué. Si le client utilise Expressplay, vous pouvez le faire à l’aide des API Expressplay pour lier le jeton Expressplay de l’utilisateur à la machine de l’utilisateur.

Vous pouvez utiliser les API de la manière suivante.

1. Générez un cookie.
1. Envoyez une requête de génération de jeton factice avec le cookie généré joint en tant que chaîne de requête (cookie=`<cookie>`) ou en tant qu’en-têtes.
1. Demandez à l’ordinateur de l’utilisateur d’envoyer une demande de licence au serveur de licences Expressplay à l’aide du jeton ci-dessus, par exemple en lisant un contenu factice.

   En cas de réussite, cette demande de licence factice associe le device_id de l’utilisateur (calculé ou généré par l’implémentation DRM sur l’appareil de l’utilisateur) au cookie dans le serveur principal Expressplay. Ce cookie est ensuite utilisé de la manière suivante :

   * Au moment de l’achat/de la location du contenu, le code interroge le serveur principal Expressplay de l’identifiant_périphérique de l’utilisateur en envoyant le cookie associé ( [https://www.expressplay.com/developer/restapi/#record-retrieval](https://www.expressplay.com/developer/restapi/#record-retrieval))
   * Envoyez une requête de génération de jeton avec la clé (CEK) du contenu acheté, l’identifiant-clé (CEKSID), les stratégies et d’autres informations, en joignant le cookie et l’identifiant_appareil ci-dessus comme, respectivement, l’identifiant `cookie` paramètre de corrélation et `deviceid` paramètre de restriction de jeton.

   * Fournissez ce jeton à l’utilisateur.

     Ce processus génère un jeton pour le contenu lié au device_id de l’utilisateur. Lorsque l’ordinateur de l’utilisateur envoie une demande de licence avec ce jeton, le serveur principal Expressplay vérifie l’id_périphérique du jeton avec l’id_périphérique de la demande de licence.

     Un exemple de serveur de droits Expressplay met en oeuvre ce workflow.
