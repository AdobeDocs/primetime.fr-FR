---
description: Pour utiliser Flash Player, assurez-vous que votre environnement répond aux exigences requises.
seo-description: Pour utiliser Flash Player, assurez-vous que votre environnement répond aux exigences requises.
seo-title: Configuration requise pour Flash Player
title: Configuration requise pour Flash Player
uuid: f181457b-2bb4-4baa-b2b7-d787f65fab75
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Configuration requise pour Flash Player{#flash-player-requirements}

Pour utiliser Flash Player, assurez-vous que votre environnement répond aux exigences requises.

<!--<a id="section_FEE654D506EC4D85AE77302AD2A27777"></a>-->

Voici la configuration requise pour Flash Player :

* Pour lire avec `Primetime.js`, installez au moins Flash Player version 23.
* Pour être invité à mettre à jour Flash Player version 23 ou ultérieure, installez au moins Flash Player version 11.0.0.

## Conditions d&#39;emballage {#section_F95FC1FEEFEA44D28C9596D2F359AFC7}

La lecture avec Flash Player nécessite les fichiers SWF suivants :

* Fichier SWF d’application principal qui gère les API du navigateur TVSDK.
* Fichier `playerProductInstall.swf` SWF qui gère l’installation et les mises à jour de Flash Player.

En outre, la lecture vidéo dans Flash nécessite un fichier de jeton d’autorisation qui peut être un fichier SWF ou un `.DAT` fichier. Le chemin d’accès aux fichiers SWF, au fichier de jeton d’autorisation, ainsi que le nom et le type de fichier de jeton peuvent être spécifiés à l’aide des API AdobePSDK.

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

