---
description: Vous pouvez définir des valeurs de contrôle ABR uniquement avec ABRControlParameters, mais vous pouvez en construire une nouvelle à tout moment.
title: Configuration des débits adaptatifs à l'aide des paramètres ABRControlParameters
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# Configurez les débits adaptatifs à l&#39;aide de ABRControlParameters {#configure-adaptive-bit-rates-using-abrcontrolparameters}

Vous pouvez définir des valeurs de contrôle ABR uniquement avec ABRControlParameters, mais vous pouvez en construire une nouvelle à tout moment.

Les conditions suivantes s&#39;appliquent à `ABRControlParameters` :

* Au moment de la construction, vous devez fournir des valeurs pour tous les paramètres.
* Après la construction, vous ne pouvez plus modifier les valeurs individuelles.
* Si les paramètres que vous spécifiez sont en dehors de la plage autorisée, un `ArgumentError` est généré.

1. Déterminez vos débits initiaux, minimaux et maximaux.
1. Déterminez la stratégie ABR :

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. Définissez les valeurs du paramètre ABR dans le constructeur `ABRControlParameters` et affectez-les au lecteur Media.

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
