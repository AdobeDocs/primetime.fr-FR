---
description: Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion de session, l’accès aux portes, etc.
title: Utilisation des cookies
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '246'
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

1. Créez un `cookieManager` et ajoutez vos cookies pour les URI à vos `cookieStore`.

   Par exemple :

   >[!IMPORTANT]
   >
   >Lorsque la redirection 302 est activée, la requête de publicité peut être redirigée vers un domaine différent du domaine auquel le cookie appartient.

   ```java
   CookieManager cookieManager= new CookieManager(); 
   CookieHandler.setDefault(cookieManager);  
   HttpCookie cookie=new HttpCookie("lang","fr"); 
   cookie.setDomain("twitter.com");  
   cookie.setPath("/"); 
   cookie.setVersion(0); 
   cookieManager.getCookieStore().add(newURI("https://twitter.com/"),cookie);
   ```

   TVSDK interroge ce cookieManager au moment de l’exécution, vérifie si des cookies sont associés à l’URL et les utilise automatiquement.

   Une autre option consiste à utiliser `cookieHeaders` in `NetworkConfiguration` pour définir une chaîne d’en-tête de cookie arbitraire à utiliser pour les requêtes. Par défaut, cet en-tête de cookie est envoyé uniquement avec les demandes clés. Pour envoyer l’en-tête du cookie avec toutes les requêtes, utilisez la méthode `NetworkConfiguration` method `setUseCookieHeadersForAllRequests`:

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
