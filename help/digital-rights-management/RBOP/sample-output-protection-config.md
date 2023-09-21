---
description: Cette section présente un exemple de configuration qui illustre les concepts et la forme de la configuration.
title: Exemple de configuration RBOP
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Exemple de configuration RBOP {#sample-rbop-configuration}

Cette section présente un exemple de configuration qui illustre les concepts et la forme de la configuration.

L’exemple de configuration JSON suivant définit une stratégie de sortie de pixel qui spécifie ce qui suit :

* Restreindre le décryptage de la vidéo aux résolutions 1080 ou antérieures
* Imposer des contraintes spécifiques pour les résolutions 720 et 480 :

   * Pour la résolution 720 : nécessite HDCP pour la sortie numérique ; nécessite *Système de gestion de génération de copies - Analogue* (CGMS-A) protection pour la sortie analogique.
   * Pour la résolution 480 : nécessite HDCP pour la sortie numérique ; ne nécessite pas de protection pour le mode analogique

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

Notez les points suivants concernant l’exemple de configuration ci-dessus :

* La variable `pixelCount` Les spécifications sont définies à un niveau dans la structure JSON, dans la variable `pixelConstraints` .

* Dans chaque spécification de nombre de pixels, la protection de sortie est spécifiée pour la sortie numérique et analogique.
* Dans les spécifications de sortie numérique, les versions HDCP sont spécifiées, bien que le client ne prenne actuellement pas en charge le contrôle de version HDCP. Pour plus d’informations, consultez la FAQ .
