---
description: Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion de session, l’accès aux portes, etc.
title: Utilisation des cookies
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Utilisation des cookies{#work-with-cookies}

Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion de session, l’accès aux portes, etc.

Voici un exemple avec un certain type d’authentification lors de l’envoi de requêtes au serveur clé :

1. Votre client se connecte à votre site web dans un navigateur et son identifiant indique qu’il est autorisé à afficher le contenu.
1. Votre application génère un jeton d’authentification en fonction de ce qui est attendu par le serveur de licences. Transmettez cette valeur à TVSDK.
1. TVSDK définit cette valeur dans l’en-tête du cookie.
1. Lorsque TVSDK envoie une requête au serveur clé pour obtenir une clé pour déchiffrer le contenu, cette requête contient la valeur d’authentification dans l’en-tête du cookie, de sorte que le serveur de clé sache que la requête est valide.

Pour utiliser des cookies :

1. Utilisez la variable `cookieHeaders` dans `NetworkConfiguration` pour définir un cookie. La variable `cookieHeaders` est un objet de métadonnées et vous pouvez ajouter des paires clé-valeur à cet objet pour l’inclure dans l’en-tête du cookie.

   Par exemple :

   ```
   var metadata:Metadata = new Metadata(); 
   metadata.setValue(“val1”, “12345”); 
   metadata.setValue(“val2”, “abcd”); 
   
   networkConfiguration.cookieHeaders = metadata;
   ```

   Par défaut, les en-têtes de cookie sont envoyés uniquement avec les demandes clés. Pour envoyer des en-têtes de cookie avec toutes les requêtes, définissez la variable `NetworkConfiguration` property `useCookieHeadersForAllRequests` sur true.

1. Pour garantir que `NetworkConfiguration` fonctionne, définissez-le comme métadonnées :

   ```
   var networkConfiguration:NetworkConfiguration = new NetworkConfiguration(); 
   networkConfiguration.forceNativeNetworking = true; 
   var resourceMetadata:Metadata = new Metadata(); 
   resourceMetadata.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                                networkConfiguration);
   ```

1. Fournir les métadonnées de l’étape précédente lorsque vous créez une `MediaResource`.

   Par exemple, si vous utilisez la variable `createFromURL` , saisissez les informations suivantes :

   ```
   var resource:MediaResource = MediaResource.createFromURL(url, resourceMetadata);
   ```
