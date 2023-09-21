---
description: Questions fréquentes sur l’utilisation de la protection de sortie basée sur la résolution.
title: FAQ sur RBOP
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# FAQ sur RBOP {#rbop-faq}

Questions fréquentes sur l’utilisation de la protection de sortie basée sur la résolution.

* **Q.** *Lors de la définition d’une exigence de sortie numérique pour une contrainte de pixel, j’obtiens des erreurs d’analyse/de formatage lorsque je quitte la version HDCP, mais je n’ai aucune exigence HDCP. Comment configurer mes exigences de sortie numérique dans ce cas ?* **A.** Comme la vérification de version HDCP n’est actuellement pas prise en charge par le client, Adobe recommande de définir la version HDCP sur `1.0`. Cela permet de s’assurer que votre configuration est correctement formatée et sémantiquement cohérente à l’avenir lorsque la vérification de version HDCP est prise en charge. Le fragment de code suivant illustre une configuration avec cette valeur HDCP.

  ```
  { "pixelConstraints":  
    [  
      { "pixelCount": 720, "digital":  
        [  
          {  
            "output": "REQUIRED", "hdcp": {"major": 1, "minor": 0}  
          }  
        ]  
      }  
    ]  
  }
  ```

* **Q.** *Les contraintes de pixels RBOP sont-elles discrètes ou basées sur une plage ?* **A.** Les contraintes de pixels RBOP sont basées sur la plage. Chaque nombre de pixels définit les exigences pour tous les nombres de pixels inférieurs ou égaux au nombre donné ou jusqu’au plus grand nombre inférieur à cette valeur s’il existe plusieurs contraintes de pixel. En d’autres termes, les valeurs s’appliquent comme seuils maximaux pour chaque nombre vertical de pixels.

  Supposons qu’un flux MBR avec des résolutions verticales de 240, 480, 600, 720 et 1080 soit transmis à votre lecteur avec les paramètres RBOP suivants.

  **Paramètres de la stratégie RBOP :**

   * 720P - HDCP requis
   * 480P - No OP

  Les règles suivantes seront appliquées à chaque variante.

  **Flux :**

   * 240, 480 : Les deux sont &lt;= 480 ; aucun OP ne doit être requis et les flux se chargent avec ou sans HDCP présent.
   * 600, 720 : les deux sont &lt;= 720 ; HDCP est requis pour la lecture
   * 1080 : > 720 ; la diffusion est bloquée (erreur renvoyée) car elle est introuvable dans les règles ci-dessus.

* **Q.** Sur certains de mes appareils Android, les restrictions de nombre de pixels que j’ai définies ne sont pas appliquées exactement comme définies. Que se passe-t-il ?

  **A.** Certains appareils Android signalent des tailles d’image légèrement supérieures à la taille normale. Pour remédier à cette situation, ajustez les tailles d’image ( `maxPixel` et `pixelCount` ) vers le haut de 20 pixels. Par exemple, ajustez les paramètres de la taille de l’image vers le haut, à partir des éléments suivants :

  ```
  { 
      "maxPixel": 800, 
      "pixelConstraints": [ 
          { "pixelCount": 532, 
            "digital": [{"output": "REQUIRED", "hdcp":{"major": 1,"minor": 0}}], 
            "analog": {"output": "REQUIRED"} 
          }, 
  ... 
  ```

  à :

  ```
  { 
      "maxPixel": 820, 
      "pixelConstraints": [ 
          { "pixelCount": 552, 
            "digital": [{"output": "REQUIRED", "hdcp":{"major": 1,"minor": 0}}], 
            "analog": {"output": "REQUIRED"} 
          }, 
  ... 
  ```

  tout au long de, pour toutes les instances de `maxPixel` et `pixelCount`.
