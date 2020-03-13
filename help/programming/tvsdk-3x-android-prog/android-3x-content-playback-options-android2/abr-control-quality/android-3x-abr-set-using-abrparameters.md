---
description: Vous pouvez définir des valeurs de contrôle ABR uniquement avec ABRControlParameters, mais vous pouvez en construire une nouvelle à tout moment.
seo-description: Vous pouvez définir des valeurs de contrôle ABR uniquement avec ABRControlParameters, mais vous pouvez en construire une nouvelle à tout moment.
seo-title: Configuration des débits adaptatifs à l’aide de ABRControlParameters
title: Configuration des débits adaptatifs à l’aide de ABRControlParameters
uuid: 283ccd3d-535b-43ca-8ca5-82d12df31798
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Configuration des débits adaptatifs à l’aide de ABRControlParameters {#configure-adaptive-bit-rates-using-abrcontrolparameters}

Vous pouvez définir des valeurs de contrôle ABR uniquement avec ABRControlParameters, mais vous pouvez en construire une nouvelle à tout moment.

Les conditions suivantes s’appliquent à `ABRControlParameters`:

* Au moment de la construction, vous devez fournir des valeurs pour tous les paramètres.
* Après la construction, vous ne pouvez plus modifier les valeurs individuelles.
* Si les paramètres que vous spécifiez ne sont pas compris dans la plage autorisée, une `ArgumentError` valeur est générée.

1. Déterminez vos débits initial, minimal et maximal.
1. Déterminer la stratégie ABR :

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. Définissez les valeurs des paramètres ABR dans le `ABRControlParameters` constructeur et affectez-les au lecteur multimédia.

   ```
   public ABRControlParameters(int initialBitRate, 
     int minBitRate, 
     int maxBitRate, 
     ABRControlParameters.ABRPolicy abrPolicy, 
     int minTrickPlayBitRate, 
     int maxTrickPlayBitRate, 
     int maxTrickPlayBandwidthUsage, 
     int maxPlayoutRate);
   ```
