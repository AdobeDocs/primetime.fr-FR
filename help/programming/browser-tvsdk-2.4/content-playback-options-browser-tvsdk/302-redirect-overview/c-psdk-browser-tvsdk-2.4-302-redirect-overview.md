---
description: L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer la charge de manière plus efficace.
seo-description: L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer la charge de manière plus efficace.
seo-title: Optimisation de la redirection HTTP 302
title: Optimisation de la redirection HTTP 302
uuid: d3009c6c-320a-4c0f-b6ba-bf6473049823
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 1%

---


# Optimisation de la redirection HTTP 302 {#http-redirect-optimization}

L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer la charge de manière plus efficace.

Si une requête de manifeste principale est redirigée et que l’optimisation de la version 302 est activée dans votre lecteur, les requêtes suivantes effectuées pour les ressources à partir de ce manifeste utiliseront l’emplacement de domaine final, ce qui évite 302 réponses supplémentaires. Cette fonction est activée par défaut et vous pouvez modifier ce paramètre.

>[!IMPORTANT]
>
>Cette fonctionnalité est uniquement prise en charge dans les navigateurs certifiés qui prennent en charge la propriété `responseURL` dans l&#39;objet `XMLHttpRequest`.

Pour les Flashs de secours, tenez compte des informations suivantes :

* Les utilisateurs finaux doivent avoir installé Adobe Flash Player version 23 ou ultérieure.
* Si l’intégrité du flux est désactivée, la redirection 302 est prise en charge uniquement sur les navigateurs certifiés.

## Désactivation de l&#39;optimisation de la redirection 302 {#disabling-redirect-optimization}

Vous pouvez utiliser la propriété useRedirectUrl pour activer la redirection 302 (true) ou la désactivation (false).

Par exemple :

```js
var networkConfiguration = new AdobePSDK.NetworkConfiguration(); 
networkConfiguration.useRedirectedUrl = false; 
 
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.networkConfiguration = networkConfiguration;; 
 
player.replaceCurrentResource(mediaResource, config);
```
