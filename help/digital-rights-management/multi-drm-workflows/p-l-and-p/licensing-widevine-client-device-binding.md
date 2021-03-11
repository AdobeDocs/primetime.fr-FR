---
description: Dans certains cas, vous pouvez empêcher les utilisateurs finaux de lire du contenu sur plusieurs périphériques lorsque le contenu est acheté ou loué. Si le client utilise Expressplay, vous pouvez le faire en utilisant les API Expressplay pour lier le jeton Expressplay de l’utilisateur à l’ordinateur de l’utilisateur.
title: Liaison de périphérique
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# Liaison de périphérique {#device-binding}

Dans certains cas, vous pouvez empêcher les utilisateurs finaux de lire du contenu sur plusieurs périphériques lorsque le contenu est acheté ou loué. Si le client utilise Expressplay, vous pouvez le faire en utilisant les API Expressplay pour lier le jeton Expressplay de l’utilisateur à l’ordinateur de l’utilisateur.

Vous pouvez utiliser les API de la manière suivante.

1. Générez un cookie.
1. Envoyez une demande de génération de jeton factice avec le cookie généré attaché en tant que chaîne de requête (cookie=`<cookie>`) ou en tant qu’en-têtes.
1. Demandez à l’ordinateur de l’utilisateur d’envoyer une demande de licence au serveur de licences Expressplay à l’aide du jeton ci-dessus, par exemple en lisant un contenu factice.

   Cette demande de licence factice associe, en cas de réussite, le device_id de l’utilisateur (calculé ou généré par l’implémentation DRM sur le périphérique de l’utilisateur) au cookie dans le serveur principal d’Expressplay. Ce cookie est ensuite utilisé de la manière suivante :

   * Au moment de l’achat/de la location du contenu, le code requête le serveur principal Expressplay de l’ID_périphérique de l’utilisateur en envoyant le cookie associé ( [https://www.expressplay.com/developer/restapi/#record-retrieval](https://www.expressplay.com/developer/restapi/#record-retrieval)).
   * Envoyez une demande de génération de jeton avec la clé de contenu acheté (CEK), l’identifiant de clé (CEKSID), les stratégies et d’autres informations, en associant le cookie et l’ID de périphérique ci-dessus comme, respectivement, le paramètre de corrélation `cookie` et le paramètre de restriction de jeton `deviceid`.

   * Fournissez ce jeton à l’utilisateur.

      Ce processus génère un jeton pour le contenu lié au device_id de l’utilisateur. Lorsque l’ordinateur de l’utilisateur envoie une demande de licence avec ce jeton, le serveur principal d’Expressplay vérifie l’ID de périphérique du jeton avec l’ID de périphérique de la demande de licence.

      Un exemple de serveur de droits Expressplay implémente ce processus.
