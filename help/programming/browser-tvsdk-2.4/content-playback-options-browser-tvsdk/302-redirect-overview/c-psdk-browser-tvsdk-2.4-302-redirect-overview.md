---
description: L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer plus efficacement la charge.
title: Optimisation des redirections HTTP 302
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Optimisation des redirections HTTP 302 {#http-redirect-optimization}

L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer plus efficacement la charge.

Si une requête de manifeste principale est redirigée et que l’optimisation 302 est activée dans votre lecteur, les requêtes suivantes effectuées pour les ressources de ce manifeste utiliseront l’emplacement de domaine final, ce qui évite 302 réponses supplémentaires. Cette fonction est activée par défaut et vous pouvez la modifier.

>[!IMPORTANT]
>
>Cette fonctionnalité est prise en charge uniquement dans les navigateurs certifiés qui prennent en charge la fonction `responseURL` dans la propriété `XMLHttpRequest` .

Pour le Flash de secours, prenez note des informations suivantes :

* Les utilisateurs finaux doivent avoir installé Adobe Flash Player version 23 ou ultérieure.
* Si l’intégrité du flux est désactivée, la redirection 302 est prise en charge uniquement sur les navigateurs certifiés.

## Désactivation de l’optimisation de la redirection 302 {#disabling-redirect-optimization}

Vous pouvez utiliser la propriété useRedirectUrl pour activer la redirection 302 (true) ou désactiver (false).

Par exemple :

```js
var networkConfiguration = new AdobePSDK.NetworkConfiguration(); 
networkConfiguration.useRedirectedUrl = false; 
 
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.networkConfiguration = networkConfiguration;; 
 
player.replaceCurrentResource(mediaResource, config);
```
