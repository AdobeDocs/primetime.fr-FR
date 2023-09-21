---
description: Vous pouvez définir des valeurs de contrôle ABR uniquement avec ABRControlParameters, mais vous pouvez en construire une nouvelle à tout moment.
title: Configuration des taux de bits adaptatifs à l’aide d’ABRControlParameters
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Configuration des taux de bits adaptatifs à l’aide d’ABRControlParameters{#configure-adaptive-bit-rates-using-abrcontrolparameters}

Vous pouvez définir des valeurs de contrôle ABR uniquement avec ABRControlParameters, mais vous pouvez en construire une nouvelle à tout moment.

Les conditions suivantes s&#39;appliquent à `ABRControlParameters`:

* Vous devez fournir des valeurs pour tous les paramètres au moment de la construction.
* Vous ne pouvez pas modifier les valeurs individuelles après l’heure de construction.
* Si les paramètres que vous spécifiez se trouvent en dehors de la plage autorisée, une `ArgumentError` est généré.

1. Décidez des débits initial, minimal et maximal.
1. Déterminer la stratégie ABR :

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. Définissez les valeurs du paramètre ABR dans la variable `ABRControlParameters` constructeur et affectez-les au lecteur multimédia.

   ```java
   public ABRControlParameters(int initialBitRate, 
     int minBitRate, 
     int maxBitRate, 
     ABRControlParameters.ABRPolicy abrPolicy, 
     int minTrickPlayBitRate, 
     int maxTrickPlayBitRate, 
     int maxTrickPlayBandwidthUsage, 
     int maxPlayoutRate);
   ```
