---
description: Vous pouvez définir des valeurs de contrôle ABR uniquement avec ABRControlParameters, mais vous pouvez en construire une nouvelle à tout moment.
seo-description: Vous pouvez définir des valeurs de contrôle ABR uniquement avec ABRControlParameters, mais vous pouvez en construire une nouvelle à tout moment.
seo-title: Configuration des débits adaptatifs à l’aide de ABRControlParameters
title: Configuration des débits adaptatifs à l’aide de ABRControlParameters
uuid: 99b7a463-327b-48bf-8244-e41467072b44
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Configuration des débits adaptatifs à l’aide de ABRControlParameters{#configure-adaptive-bit-rates-using-abrcontrolparameters}

Vous pouvez définir des valeurs de contrôle ABR uniquement avec ABRControlParameters, mais vous pouvez en construire une nouvelle à tout moment.

Les conditions suivantes s’appliquent à `ABRControlParameters`:

* Vous devez fournir des valeurs pour tous les paramètres au moment de la construction.
* Vous ne pouvez pas modifier les valeurs individuelles après la construction.
* Si les paramètres que vous spécifiez ne sont pas compris dans la plage autorisée, une `ArgumentError` valeur est générée.

1. Déterminer la stratégie ABR :

   * `ABRControlParameters.CONSERVATIVE_POLICY`
   * `ABRControlParameters.MODERATE_POLICY`
   * `ABRControlParameters.AGGRESSIVE_POLICY`

1. Définissez les valeurs des paramètres ABR dans le `ABRControlParameters` constructeur et affectez-les au lecteur multimédia.

   ```js
   var abrParams = new AdobePSDK.ABRControlParameters(); 
   abrParams.initialBitRate = nInitialBitRate; 
   abrParams.minBitRate = nMinBitRate; 
   abrParams.maxBitRate = nMaxBitRate; 
   abrParams.abrPolicy = eABRPolicy; 
   player.abrControlParameters = abrParams;
   ```

