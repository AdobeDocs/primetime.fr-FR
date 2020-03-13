---
description: Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion des sessions, l’accès aux portes, etc.
seo-description: Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion des sessions, l’accès aux portes, etc.
seo-title: Utilisation des cookies
title: Utilisation des cookies
uuid: f060b520-ceec-48ca-929f-683566fe6ae7
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Utilisation des cookies{#work-with-cookies}

Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion des sessions, l’accès aux portes, etc.

Voici un exemple avec un certain type d’authentification lors de l’envoi de requêtes au serveur de clés :

1. Votre client se connecte à votre site Web dans un navigateur et sa connexion indique qu’il est autorisé à du contenu.
1. Votre application génère un jeton d’authentification, en fonction des attentes du serveur de licences. Transmettez cette valeur à TVSDK.
1. TVSDK définit cette valeur dans l’en-tête du cookie.
1. Lorsque TVSDK envoie une requête au serveur de clés pour obtenir une clé afin de déchiffrer le contenu, cette requête contient la valeur d’authentification dans l’en-tête du cookie. Le serveur de clés sait donc que la requête est valide.

Pour utiliser les cookies :

1. Créez un `cookieManager` et ajoutez vos cookies pour les URI à votre `cookieStore`application.

   Par exemple :

   >[!IMPORTANT]
   >
   >Lorsque la redirection 302 est activée, la demande d’annonce peut être redirigée vers un domaine différent du domaine auquel le cookie appartient.

   ```java
   CookieManager cookieManager= new CookieManager(); 
   CookieHandler.setDefault(cookieManager);  
   HttpCookie cookie=new HttpCookie("lang","fr"); 
   cookie.setDomain("twitter.com");  
   cookie.setPath("/"); 
   cookie.setVersion(0); 
   cookieManager.getCookieStore().add(newURI("https://twitter.com/"),cookie);
   ```

   Le TVSDK  ce cookieManager au moment de l’exécution, vérifie s’il existe des cookies associés à l’URL et les utilise automatiquement.

   Une autre option consiste à utiliser `cookieHeaders` dans `NetworkConfiguration` pour définir une chaîne d&#39;en-tête de cookie arbitraire à utiliser pour les requêtes. Par défaut, cet en-tête de cookie est envoyé uniquement avec les requêtes de clé. Pour envoyer l’en-tête du cookie avec toutes les requêtes, utilisez la `NetworkConfiguration` méthode `setUseCookieHeadersForAllRequests`:

   ```java
   NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
   
   Metadata cookie = new MetadataNode(); 
   cookie.setValue("reqPayload", “1234567”); 
   networkConfiguration.setCookieHeaders(cookie); 
   networkConfiguration.setUseCookieHeadersForAllRequests( true ); 
   
   // Set NetworkConfiguration as Metadata:                                                                   
   MetadataNode resourceMetadata = new MetadataNode();  
   resourceMetadata.setNode(DefaultMetadataKeys.NETWORK_CONFIGURATION.getValue(),  
                            networkConfiguration); 
   
   // Call MediaResource.createFromURL to set the metadata: 
   MediaResource resource = MediaResource.createFromURL(url, resourceMetadata); 
    // Load the resource 
   mediaPlayer.replaceCurrentItem(resource);
   ```

