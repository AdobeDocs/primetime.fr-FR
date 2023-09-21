---
description: Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion de session, l’accès aux portes, etc.
title: Utilisation des cookies
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Utilisation des cookies {#work-with-cookies}

Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion de session, l’accès aux portes, etc.

Voici un exemple de requête au serveur clé avec une authentification :

1. Votre client se connecte à votre site web dans un navigateur et son login indique que ce client est autorisé à afficher le contenu.
1. Selon les attentes du serveur de licences, votre application génère un jeton d’authentification.

   Cette valeur est transmise à TVSDK.
1. TVSDK définit cette valeur dans l’en-tête du cookie.
1. Lorsque TVSDK envoie une requête au serveur de clés pour obtenir une clé pour déchiffrer le contenu, la requête contient la valeur d’authentification dans l’en-tête du cookie.

   Le serveur de clés sait que la requête est valide.

Pour utiliser des cookies :

1. Créez un `cookieManager` et ajoutez vos cookies pour les URI à votre cookieStore.

   Par exemple :

   ```java
   CookieManager cookieManager=new CookieManager(); 
   CookieHandler.setDefault(cookieManager);  
   HttpCookie cookie=new HttpCookie("lang","fr"); 
   cookie.setDomain("twitter.com");  
   cookie.setPath("/"); 
   cookie.setVersion(0); 
   cookieManager.getCookieStore().add(newURI("https://twitter.com/"),cookie);
   ```

   >[!TIP]
   >
   >Lorsque la redirection 302 est activée, la requête de publicité peut être redirigée vers un domaine différent du domaine auquel le cookie appartient.

   TVSDK interroge cette `cookieManager` au moment de l’exécution, vérifie si des cookies sont associés à l’URL et utilise automatiquement ces cookies.

   Si les cookies doivent être mis à jour dans l’application au cours de la lecture, n’utilisez pas `networkConfiguration.setCookieHeaders` API lors de la mise à jour se produit dans le magasin de cookies JAVA.

   `networkConfiguration.setCookieHeaders` L’API définit les cookies sur le cookieStore C++ de TVSDK.

   Lors de l’utilisation de cookies JAVA et de leur partage entre l’application et TVSDK, utilisez JAVA CookieStore pour gérer les cookies uniquement.

   Avant d’initialiser la lecture, définissez les cookies sur CookieStore à l’aide du gestionnaire de cookies comme indiqué ci-dessus.

   Le cookie stocké dans CookieStore sera automatiquement récupéré par TVSDK.

   Si une valeur de cookie doit être mise à jour ultérieurement pendant la lecture, appelez la même méthode d’ajout de CookieStore avec la même clé et un nouveau champ de valeur.

   Également défini
   `networkConfiguration.setReadSetCookieHeader`(false) avant d’appeler
   `config.setNetworkConfiguration(networkConfiguration)`

   >[!NOTE]
   >
   >Après avoir défini &quot;setReadSetCookieHeader&quot; sur false, définissez les cookies pour les demandes de clés à l’aide du gestionnaire de cookies JAVA.

   `onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent)`
Cette API de rappel est déclenchée chaque fois qu’il y a une mise à jour des cookies C++ (cookies issus de la réponse http). L’application doit écouter ce rappel et peut mettre à jour son JAVA CookieStore en conséquence afin que ses appels réseau dans JAVA puissent utiliser les cookies comme ci-dessous :

   ```
   private final CookiesUpdatedEventListener cookiesUpdatedEventListener = new CookiesUpdatedEventListener() {
   @Override
   public void onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent) {
   List<HttpCookie> cookies = cookiesUpdatedEvent.getHttpCookies();
   for(int i = 0; i < cookies.size(); i++)
   { HttpCookie c = cookies.get(i); // To set this cookie on to the cookie store //c.setValue("newValue"); //If you want to modify the value of the cookie URI myuri = URI.create(cookiesUpdatedEvent.getDomainString()); cookieManager.getCookieStore().add(myuri,c); }
   }
   }
   ```
