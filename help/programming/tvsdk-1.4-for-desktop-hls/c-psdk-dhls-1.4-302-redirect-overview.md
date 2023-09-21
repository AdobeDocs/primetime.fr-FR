---
description: L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer plus efficacement la charge.
title: Optimisation des redirections HTTP 302
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Optimisation des redirections HTTP 302{#http-redirect-optimization}

L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer plus efficacement la charge.

Si une requête de manifeste principale est redirigée et que l’optimisation 302 est activée dans votre lecteur, les requêtes suivantes effectuées pour les ressources de ce manifeste utiliseront l’emplacement de domaine final, ce qui évite 302 réponses supplémentaires.

Cette fonctionnalité est désactivée par défaut et vous pouvez la modifier.

Si vous activez cette fonction, elle ne fonctionne correctement que si *all* des conditions suivantes sont vraies ; dans le cas contraire, aucune optimisation de la redirection ne se produit et 302 réponses continuent à se produire :

* Votre application a été compilée pour Adobe Flash Player 11.8, à l’aide de `-swf-version` 21 ou version ultérieure.
* Les utilisateurs finaux disposent d’Adobe Flash Player 11.8 ou d’une version ultérieure.

>[!IMPORTANT]
>
>Pour vous assurer que les cookies sont transmis avec les demandes d’annonce, désactivez la redirection 302. Lorsque la redirection 302 est activée, la requête de publicité peut être redirigée vers un domaine différent du domaine d’origine du cookie.

## Désactivation ou activation de l’optimisation de la redirection 302 {#section_D6687FC44C61446F878008B629A5FA19}

Utilisez la variable `useRedirectedUrl` pour activer la redirection 302 (true) ou la désactiver (false).

<!--<a id="example_B886777252B745AAB48B1FCC42C97A25"></a>-->

Par exemple :

```
// Set useRedirectedUrl property to true 
var networkConfiguration = new NetworkConfiguration(); 
networkConfiguration.useRedirectedUrl = true; 
  
//Set NetworkConfiguration as Metadata: 
var result:Metadata = new Metadata(); 
result.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                   networkConfiguration); 
  
var mediaResource = new MediaResource( url, MediaResourceType.HLS, result); 
  
// load the resource 
mediaPlayer.replaceCurrentResource( mediaResource, mediaPlayerItemConfig );
```
