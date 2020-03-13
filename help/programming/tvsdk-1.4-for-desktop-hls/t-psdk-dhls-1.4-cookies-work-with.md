---
description: Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion des sessions, l’accès aux portes, etc.
seo-description: Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion des sessions, l’accès aux portes, etc.
seo-title: Utilisation des cookies
title: Utilisation des cookies
uuid: 7586a5a7-9914-403b-86a9-fbdd28664b07
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Utilisation des cookies{#work-with-cookies}

Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion des sessions, l’accès aux portes, etc.

Voici un exemple avec un certain type d’authentification lors de l’envoi de requêtes au serveur de clés :

1. Votre client se connecte à votre site Web dans un navigateur et sa connexion indique qu’il est autorisé à du contenu.
1. Votre application génère un jeton d’authentification, en fonction des attentes du serveur de licences. Transmettez cette valeur à TVSDK.
1. TVSDK définit cette valeur dans l’en-tête du cookie.
1. Lorsque TVSDK envoie une requête au serveur de clés pour obtenir une clé afin de déchiffrer le contenu, cette requête contient la valeur d’authentification dans l’en-tête du cookie. Le serveur de clés sait donc que la requête est valide.

Pour utiliser les cookies :

1. Utilisez la `cookieHeaders` propriété dans `NetworkConfiguration` pour définir un cookie. La `cookieHeaders` propriété est un objet de métadonnées et vous pouvez ajouter des paires clé-valeur à cet objet pour l’inclure dans l’en-tête du cookie.

   Par exemple :

   ```
   var metadata:Metadata = new Metadata(); 
   metadata.setValue(“val1”, “12345”); 
   metadata.setValue(“val2”, “abcd”); 
   
   networkConfiguration.cookieHeaders = metadata;
   ```

   Par défaut, les en-têtes de cookie sont envoyés uniquement avec les requêtes de clé. Pour envoyer des en-têtes de cookie avec toutes les requêtes, définissez la `NetworkConfiguration` propriété `useCookieHeadersForAllRequests` sur true.

1. Pour vous assurer que `NetworkConfiguration` fonctionne, définissez-le comme des métadonnées :

   ```
   var networkConfiguration:NetworkConfiguration = new NetworkConfiguration(); 
   networkConfiguration.forceNativeNetworking = true; 
   var resourceMetadata:Metadata = new Metadata(); 
   resourceMetadata.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                                networkConfiguration);
   ```

1. Fournissez les métadonnées de l’étape précédente lorsque vous créez une `MediaResource`.

   Par exemple, si vous utilisez la `createFromURL` méthode, saisissez les informations suivantes :

   ```
   var resource:MediaResource = MediaResource.createFromURL(url, resourceMetadata);
   ```

