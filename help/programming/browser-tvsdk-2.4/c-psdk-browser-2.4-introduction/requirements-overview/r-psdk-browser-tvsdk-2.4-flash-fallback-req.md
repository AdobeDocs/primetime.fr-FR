---
description: Pour utiliser le Flash Player, assurez-vous que votre environnement répond aux exigences requises.
seo-description: Pour utiliser le Flash Player, assurez-vous que votre environnement répond aux exigences requises.
seo-title: Flash Player requis
title: Flash Player requis
uuid: f181457b-2bb4-4baa-b2b7-d787f65fab75
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 1%

---


# Exigences du Flash Player{#flash-player-requirements}

Pour utiliser le Flash Player, assurez-vous que votre environnement répond aux exigences requises.

<!--<a id="section_FEE654D506EC4D85AE77302AD2A27777"></a>-->

Voici les conditions requises pour le Flash Player :

* Pour lire avec `Primetime.js`, installez au moins la version 23 du Flash Player.
* Pour être invité à fournir des mises à jour vers la version 23 ou ultérieure du Flash Player, installez au moins Flash Player version 11.0.0.

## Exigences en matière d&#39;emballage {#section_F95FC1FEEFEA44D28C9596D2F359AFC7}

La lecture avec Flash Player nécessite les fichiers SWF suivants :

* Fichier SWF d’application principal qui gère les API du navigateur TVSDK.
* Fichier SWF `playerProductInstall.swf` qui gère l’installation et les mises à jour des Flashs Player.

En outre, la lecture vidéo dans le Flash nécessite un fichier de jeton d’autorisation qui peut être un fichier SWF ou un fichier `.DAT`. Le chemin d’accès aux fichiers SWF, au fichier de jeton d’autorisation, ainsi que le nom et le type de fichier de jeton peuvent être spécifiés à l’aide des API AdobePSDK.

Par exemple :

```js
// Set relative or http path to directory containing SWF.  
// Defaults to current directory for the html page. 
AdobePSDK.setSWFPath(<swfPath>); 
 
// Set the relative or http path to directory containing token file(s). 
// Defaults to SWFPath + "token/". 
AdobePSDK.setAuthorizationTokenPath(<authorizationTokenPath>); 
 
// Set the name of the token file, do not include any path in this string. 
AdobePSDK.setAuthorizationTokenFilename("hlsaf_localhost.swf"); 
 
//Set the token type, "DAT" or "SWF". Defaults to "DAT" 
AdobePSDK.setAuthorizationTokenType("SWF");
```

