---
description: 'null'
seo-description: 'null'
seo-title: Règles métier de la démonstration de modèle d’utilisation
title: Règles métier de la démonstration de modèle d’utilisation
uuid: c55f85be-5ecb-4a78-b47d-7001ec207d3a
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Règles métier de démonstration du modèle d’utilisation{#usage-model-demo-business-rules}

Lorsqu’un utilisateur demande une licence, le serveur d’implémentation de référence vérifie les métadonnées envoyées par le client, afin de déterminer si le contenu a été compressé à l’aide de la propriété `RI_UsageModelDemo`. Si tel est le cas, le serveur applique les règles de fonctionnement suivantes.

* Si l’une des stratégies DRM nécessite une authentification :

   * Si la requête contient un jeton d’authentification valide, recherchez le nom de l’utilisateur dans la table de base de données du client.

      Si vous ne parvenez pas à localiser le nom de l’utilisateur, renseignez les tâches suivantes :

      * Si la propriété `Customer.IsSubscriber` est définie sur `true`, vous devez générer une licence pour le modèle d&#39;utilisation *`Subscription`* et l&#39;envoyer à l&#39;utilisateur.

      * Recherchez un enregistrement dans la table de base de données `CustomerAuthorization` pour le nom de l’utilisateur et l’ID de contenu.

      Si vous pouvez localiser l’enregistrement de l’utilisateur, effectuez les tâches suivantes :

      * Si la propriété `CustomerAuthorization.UsageType` est définie sur `DTO`, générez une licence pour le modèle d’utilisation DTO et envoyez-la à l’utilisateur.

      * Si la propriété `CustomerAuthorization.UsageType` est définie sur `VOD`, générez une licence pour le modèle d’utilisation VOD et envoyez-la à l’utilisateur.

      Si aucune des stratégies DRM n’autorise l’accès anonyme, effectuez les tâches suivantes :

      * Si la requête ne contient pas de jeton d’authentification valide, vous devez renvoyer une erreur &quot;authentification requise&quot;.
      * Sinon, renvoyez une erreur &quot;non autorisé&quot;.



* Si l’une des stratégies DRM autorise l’accès anonyme, générez une licence pour le modèle d’utilisation financé par la publicité et envoyez-la à l’utilisateur.

