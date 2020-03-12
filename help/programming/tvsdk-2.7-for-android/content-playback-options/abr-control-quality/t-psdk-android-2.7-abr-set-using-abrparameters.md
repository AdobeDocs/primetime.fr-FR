---
description: Vous pouvez définir des valeurs de contrôle ABR uniquement avec ABRControlParameters, mais vous pouvez en construire une nouvelle à tout moment.
seo-description: Vous pouvez définir des valeurs de contrôle ABR uniquement avec ABRControlParameters, mais vous pouvez en construire une nouvelle à tout moment.
seo-title: Configuration des débits adaptatifs à l’aide de ABRControlParameters
title: Configuration des débits adaptatifs à l’aide de ABRControlParameters
uuid: 7084e954-196b-492e-846f-f8b36bed13a9
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

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

