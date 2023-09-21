---
description: Vous pouvez utiliser TVSDK pour envoyer des données arbitraires dans des en-têtes de cookie pour la gestion de session, l’accès aux portes, etc.
title: Utilisation des cookies
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '236'
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

Créez un `cookieManager` et ajoutez vos cookies pour les URI à votre cookieStore.

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

L’événement MediaPlayerEvent.COOKIES_UPDATED est appelé lorsque les cookies C++ sont mis à jour. Ce cookieUpdatedEvent comporte une méthode getCookieString() qui renvoie une valeur de chaîne pour le cookie.

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
