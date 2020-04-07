---
description: Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion des sessions, l’accès aux portes, etc.
seo-description: Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion des sessions, l’accès aux portes, etc.
seo-title: Utilisation des cookies
title: Utilisation des cookies
uuid: 618bc59a-032d-445e-a867-ed2bf260570d
translation-type: tm+mt
source-git-commit: 5ada8632a7a5e3cb5d795dc42110844244656095

---


# Utilisation des cookies {#work-with-cookies}

Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion des sessions, l’accès aux portes, etc.

Voici un exemple de requête au serveur de clés avec une certaine authentification :

1. Votre client se connecte à votre site Web dans un navigateur et sa connexion indique que ce client est autorisé à du contenu.
1. En fonction des attentes du serveur de licences, votre application génère un jeton d’authentification.

   Cette valeur est transmise à TVSDK.
1. TVSDK définit cette valeur dans l’en-tête du cookie.
1. Lorsque TVSDK envoie une requête au serveur de clés pour obtenir une clé afin de déchiffrer le contenu, la requête contient la valeur d’authentification dans l’en-tête du cookie.

   Le serveur de clés sait que la requête est valide.

Pour utiliser les cookies :

1. Créez un cookie `cookieManager` et ajoutez-y vos cookies pour les URI.

   Par exemple :

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
   >Lorsque la redirection 302 est activée, la demande d’annonce peut être redirigée vers un domaine différent du domaine auquel le cookie appartient.

   Le TVSDK  ceci `cookieManager` au moment de l’exécution, vérifie s’il existe des cookies associés à l’URL et les utilise automatiquement.

   Si les cookies doivent être mis à jour dans l’application au cours de la lecture, n’utilisez pas `networkConfiguration.setCookieHeaders` l’API car la mise à jour aura lieu dans le magasin de cookies JAVA.

   `networkConfiguration.setCookieHeaders` L’API définit les cookies sur le cookieStore C++ de TVSDK.

   Lorsque vous utilisez des cookies JAVA et les partagez entre Application et TVSDK, utilisez JAVA CookieStore pour gérer uniquement les cookies.

   Avant d’initialiser la lecture, définissez les cookies sur le magasin de cookies à l’aide du Gestionnaire de cookies, comme indiqué ci-dessus.

   Le cookie stocké dans CookieStore sera automatiquement récupéré par TVSDK.

   Si une valeur de cookie doit être mise à jour ultérieurement pendant la lecture, appelez la même méthode d’ajout de CookieStore avec la même clé et un nouveau champ de valeur.

   Également défini
   `networkConfiguration.setReadSetCookieHeader`(false) avant d’appeler
   `config.setNetworkConfiguration(networkConfiguration)`

   >[!NOTE]
   >
   >Après avoir défini cet &#39;setReadSetCookieHeader&#39; sur false, définissez les cookies pour les requêtes de clés à l’aide du gestionnaire de cookies JAVA.

   `onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent)`
Cette API de rappel est déclenchée chaque fois qu’il existe une mise à jour dans les cookies C++ (cookies provenant d’une réponse http). L’application doit écouter ce rappel et peut mettre à jour son magasin de cookies JAVA en conséquence afin que ses appels réseau dans JAVA puissent utiliser les cookies comme suit :

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
