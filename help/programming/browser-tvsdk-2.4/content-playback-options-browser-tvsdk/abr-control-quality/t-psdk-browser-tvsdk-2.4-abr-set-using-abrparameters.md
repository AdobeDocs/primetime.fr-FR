---
description: Vous pouvez définir des valeurs de contrôle ABR uniquement avec ABRControlParameters, mais vous pouvez en construire une nouvelle à tout moment.
title: Configuration des taux de bits adaptatifs à l’aide d’ABRControlParameters
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# Configuration des taux de bits adaptatifs à l’aide d’ABRControlParameters{#configure-adaptive-bit-rates-using-abrcontrolparameters}

Vous pouvez définir des valeurs de contrôle ABR uniquement avec ABRControlParameters, mais vous pouvez en construire une nouvelle à tout moment.

Les conditions suivantes s&#39;appliquent à `ABRControlParameters`:

* Vous devez fournir des valeurs pour tous les paramètres au moment de la construction.
* Vous ne pouvez pas modifier les valeurs individuelles après l’heure de construction.
* Si les paramètres que vous spécifiez se trouvent en dehors de la plage autorisée, une `ArgumentError` est généré.

1. Déterminer la stratégie ABR :

   * `ABRControlParameters.CONSERVATIVE_POLICY`
   * `ABRControlParameters.MODERATE_POLICY`
   * `ABRControlParameters.AGGRESSIVE_POLICY`

1. Définissez les valeurs du paramètre ABR dans la variable `ABRControlParameters` constructeur et affectez-les au lecteur multimédia.

   ```js
   var abrParams = new AdobePSDK.ABRControlParameters(); 
   abrParams.initialBitRate = nInitialBitRate; 
   abrParams.minBitRate = nMinBitRate; 
   abrParams.maxBitRate = nMaxBitRate; 
   abrParams.abrPolicy = eABRPolicy; 
   player.abrControlParameters = abrParams;
   ```
