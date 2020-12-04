---
description: L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer la charge de manière plus efficace.
seo-description: L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer la charge de manière plus efficace.
seo-title: Optimisation de la redirection HTTP 302
title: Optimisation de la redirection HTTP 302
uuid: 58593d5f-a639-4d87-9589-dba6b2dbba38
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# Optimisation de la redirection HTTP 302{#http-redirect-optimization}

L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer la charge de manière plus efficace.

Si une requête de manifeste principale est redirigée et que l’optimisation de la version 302 est activée dans votre lecteur, les requêtes suivantes effectuées pour les ressources à partir de ce manifeste utiliseront l’emplacement de domaine final, ce qui évite 302 réponses supplémentaires.

Cette fonction est désactivée par défaut et vous pouvez modifier ce paramètre.

Si vous activez cette fonction, elle ne fonctionne correctement que si *toutes* des conditions suivantes sont vraies ; dans le cas contraire, aucune optimisation de la redirection n’est effectuée et 302 réponses continuent à se produire :

* Votre application a été compilée pour Adobe Flash Player 11.8, en utilisant `-swf-version` 21 ou une version ultérieure.
* Les utilisateurs finaux ont installé Adobe Flash Player 11.8 ou version ultérieure.

>[!IMPORTANT]
>
>Pour vous assurer que les cookies sont transmis avec les demandes d’annonce, désactivez la redirection 302. Lorsque la redirection 302 est activée, la demande d’annonce peut être redirigée vers un domaine différent du domaine d’origine du cookie.

## Désactivation ou activation de l&#39;optimisation de la redirection 302 {#section_D6687FC44C61446F878008B629A5FA19}

Utilisez la propriété `useRedirectedUrl` pour activer la redirection 302 (true) ou la désactiver (false).

<!--<a id="example_B886777252B745AAB48B1FCC42C97A25"></a>-->

Par exemple :

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

