---
description: 'null'
seo-description: 'null'
seo-title: Règles métier de la démonstration de modèle d’utilisation
title: Règles métier de la démonstration de modèle d’utilisation
uuid: c55f85be-5ecb-4a78-b47d-7001ec207d3a
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Règles métier de la démonstration de modèle d’utilisation{#usage-model-demo-business-rules}

Lorsqu’un utilisateur demande une licence, le serveur d’implémentation des références vérifie les métadonnées envoyées par le client, afin de déterminer si le contenu a été compressé à l’aide de la `RI_UsageModelDemo` propriété. Si tel est le cas, le serveur applique les règles de fonctionnement suivantes.

* Si l’une des stratégies DRM nécessite une authentification :

   * Si la requête contient un jeton d’authentification valide, recherchez le nom de l’utilisateur dans la table de base de données du client.

      Si vous ne parvenez pas à localiser le nom de l’utilisateur, renseignez les tâches suivantes :

      * Si la `Customer.IsSubscriber` propriété est définie sur `true`, vous devez générer une licence pour le modèle d’ *`Subscription`* utilisation et l’envoyer à l’utilisateur.

      * Recherchez un enregistrement dans la table de la `CustomerAuthorization` base de données pour le nom de l’utilisateur et l’identifiant de contenu.
      Si vous pouvez localiser l’enregistrement de l’utilisateur, effectuez les tâches suivantes :

      * Si la `CustomerAuthorization.UsageType` propriété est définie sur `DTO`, générez une licence pour le modèle d’utilisation DTO et envoyez-la à l’utilisateur.

      * Si la `CustomerAuthorization.UsageType` propriété est définie sur `VOD`, générez une licence pour le modèle d’utilisation VOD et envoyez-la à l’utilisateur.
      Si aucune des stratégies DRM n’autorise l’accès anonyme, effectuez les tâches suivantes :

      * Si la requête ne contient pas de jeton d’authentification valide, vous devez renvoyer une erreur &quot;authentification requise&quot;.
      * Sinon, renvoyez une erreur &quot;non autorisé&quot;.



* Si l’une des stratégies DRM autorise l’accès anonyme, générez une licence pour le modèle d’utilisation financé par la publicité et envoyez-la à l’utilisateur.

