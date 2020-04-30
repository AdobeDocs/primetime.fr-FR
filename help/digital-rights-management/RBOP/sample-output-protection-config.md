---
description: Cette section présente un exemple de configuration qui illustre les concepts et la forme de la configuration.
seo-description: Cette section présente un exemple de configuration qui illustre les concepts et la forme de la configuration.
seo-title: Exemple de configuration RBOP
title: Exemple de configuration RBOP
uuid: fa5ead93-36c5-4ad1-947b-c4f1f2632d9b
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Exemple de configuration RBOP {#sample-rbop-configuration}

Cette section présente un exemple de configuration qui illustre les concepts et la forme de la configuration.

L’exemple de configuration JSON suivant définit une stratégie de sortie de pixels qui spécifie les éléments suivants :

* Limiter le déchiffrement de la vidéo aux résolutions de 1080 ou moins
* Imposer des contraintes spécifiques aux résolutions 720 et 480 :

   * Pour la résolution 720 : exiger le HDCP pour la sortie numérique ; nécessitent une protection *Copy Generation Management System - Analog* (CGMS-A) pour une sortie analogique.
   * Pour la résolution 480 : exiger le HDCP pour la sortie numérique ; ne nécessitent pas de protection pour l&#39;analogique

```
{ 
  "pixelConstraints":  
    [ 
      { 
        "pixelCount": 720, 
        "digital": 
          [ 
            {"output": "REQUIRED", "hdcp": {"major": 1, "minor": 0}} 
          ], 
        "analog": {"output": "REQUIRED_CGMSA"} 
      }, 
      { 
        "pixelCount": 480, 
        "digital":  
          [ 
            {"output": "REQUIRED", "hdcp": {"major": 1, "minor": 0}} 
          ], 
        "analog": {"output": "NO_PROTECTION"} 
      } 
    ], 
  "maxPixel": 1080 
}
```

Tenez compte des points suivants concernant l’exemple de configuration ci-dessus :

* Les `pixelCount` spécifications sont un niveau inférieur dans la structure JSON, dans la `pixelConstraints` section.

* Dans chaque spécification de nombre de pixels, la protection de sortie est spécifiée pour la sortie numérique et analogique.
* Dans les spécifications de sortie numérique, les versions HDCP sont spécifiées, bien que le client ne prenne pas actuellement en charge le contrôle de version HDCP. Consultez la FAQ pour plus d&#39;informations.

