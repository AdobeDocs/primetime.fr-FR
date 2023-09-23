---
title: Règles de fonctionnement de démonstration du modèle d’utilisation
description: Règles de fonctionnement de démonstration du modèle d’utilisation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Règles de fonctionnement de démonstration du modèle d’utilisation{#usage-model-demo-business-rules}

Lorsqu’un utilisateur demande une licence, le serveur de mise en oeuvre de référence vérifie les métadonnées envoyées par le client, afin de déterminer si le contenu a été compilé à l’aide de la variable `RI_UsageModelDemo` . Si tel est le cas, le serveur applique les règles de fonctionnement suivantes.

* Si l’une des stratégies DRM nécessite une authentification :

   * Si la requête contient un jeton d’authentification valide, recherchez le nom de l’utilisateur dans la table de la base de données client.

     Si vous ne pouvez pas localiser le nom de l’utilisateur, effectuez les tâches suivantes :

      * Si la variable `Customer.IsSubscriber` est définie sur `true`, vous devez générer une licence pour le *`Subscription`* modèle d’utilisation et envoyez-le à l’utilisateur.

      * Recherchez un enregistrement dans le `CustomerAuthorization` table de base de données pour le nom de l’utilisateur et l’identifiant du contenu.

     Si vous pouvez localiser l’enregistrement de l’utilisateur, effectuez les tâches suivantes :

      * Si la variable `CustomerAuthorization.UsageType` est définie sur `DTO`, générez une licence pour le modèle d’utilisation du DTO et envoyez-la à l’utilisateur.

      * Si la variable `CustomerAuthorization.UsageType` est définie sur `VOD`, générez une licence pour le modèle d’utilisation VOD et envoyez-la à l’utilisateur.

     Si aucune des stratégies DRM ne permet l’accès anonyme, effectuez les tâches suivantes :

      * Si la requête ne contient pas de jeton d’authentification valide, vous devez renvoyer une erreur &quot;authentification requise&quot;.
      * Sinon, renvoie une erreur &quot;non autorisé&quot;.

* Si l’une des politiques DRM permet un accès anonyme, générez une licence pour le modèle d’utilisation financé par l’annonce et envoyez-la à l’utilisateur.
