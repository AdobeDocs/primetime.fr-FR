---
description: Pour utiliser Flash Player, assurez-vous que votre environnement répond aux exigences nécessaires.
title: Exigences en matière de Flash Player
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Exigences en matière de Flash Player{#flash-player-requirements}

Pour utiliser Flash Player, assurez-vous que votre environnement répond aux exigences nécessaires.

<!--<a id="section_FEE654D506EC4D85AE77302AD2A27777"></a>-->

Voici les exigences du Flash Player :

* Pour lire avec `Primetime.js`, installez au moins Flash Player version 23.
* Pour être invité à fournir des mises à jour de la version 23 ou ultérieure de Flash Player, installez au moins la version 11.0.0 de Flash Player.

## Exigences de groupement {#section_F95FC1FEEFEA44D28C9596D2F359AFC7}

La lecture avec Flash Player nécessite les fichiers SWF suivants :

* Le fichier de SWF d’application principal qui gère les API Browser TVSDK.
* La variable `playerProductInstall.swf` Fichier SWF qui gère l’installation et les mises à jour des Flashs Player.

En outre, la lecture vidéo en Flash nécessite un fichier de jeton d’autorisation, qui peut être un SWF ou un `.DAT` fichier . Le chemin d’accès aux fichiers du SWF, au fichier de jeton d’autorisation, ainsi qu’au nom et au type du fichier de jeton peuvent être spécifiés à l’aide des API AdobePSDK.

Par exemple :

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
