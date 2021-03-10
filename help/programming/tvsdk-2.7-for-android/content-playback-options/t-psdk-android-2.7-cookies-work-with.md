---
description: Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion de session, l’accès aux portes, etc.
title: Utilisation des cookies
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# Utilisation de cookies {#work-with-cookies}

Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion de session, l’accès aux portes, etc.

Voici un exemple de demande au serveur clé avec une certaine authentification :

1. Votre client se connecte à votre site Web dans un navigateur et sa connexion indique que ce client est autorisé à vue du contenu.
1. En fonction des attentes du serveur de licences, votre application génère un jeton d’authentification.

   Cette valeur est transmise à TVSDK.
1. TVSDK définit cette valeur dans l’en-tête du cookie.
1. Lorsque TVSDK envoie une requête au serveur de clés pour obtenir une clé pour déchiffrer le contenu, la requête contient la valeur d’authentification dans l’en-tête du cookie.

   Le serveur de clés sait que la requête est valide.

Pour utiliser des cookies :

Créez un `cookieManager` et ajoutez vos cookies pour les URI à votre cookieStore.

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

TVSDK requête ce `cookieManager` au moment de l’exécution, vérifie si des cookies sont associés à l’URL et les utilise automatiquement.

Le événement MediaPlayerEvent.COOKIES_UPDATED est appelé lorsque les cookies C++ sont mis à jour. Cette variable cookiesUpdateEvent possède une méthode getCookieString() qui renvoie une valeur de chaîne pour le cookie.

Voici un exemple de fragment de code :

```
private final CookiesUpdatedEventListener cookiesUpdatedEventListener = new CookiesUpdatedEventListener()  
{ 
@Override 
public void onCookiesUpdated(CookiesUpdatedEvent cookiesUpdatedEvent) 
 { 
 String cookieStr = cookiesUpdatedEvent.getCookieString();  
 logger.i(LOG_TAG + "::MediaPlayer.CookiesUpdatedEventListener#onCookiesUpdated()", "cookieStr " + cookieStr);  
 }  
};
```

