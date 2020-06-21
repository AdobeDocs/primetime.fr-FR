---
description: Questions fréquentes sur l’utilisation de la protection de sortie basée sur la résolution.
seo-description: Questions fréquentes sur l’utilisation de la protection de sortie basée sur la résolution.
seo-title: FAQ RBOP
title: FAQ RBOP
uuid: 7dcd337c-369a-474c-8768-409c48b5cee5
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# FAQ RBOP {#rbop-faq}

Questions fréquentes sur l’utilisation de la protection de sortie basée sur la résolution.

* **Q.** Lors de la *définition d&#39;une exigence de sortie numérique pour une contrainte de pixels, je reçois des erreurs d&#39;analyse/formatage lorsque je quitte la version HDCP, mais je n&#39;ai aucune exigence HDCP. Comment dois-je configurer mes exigences de sortie numérique dans ce cas ?* **R.** Comme la vérification de version HDCP n&#39;est pas prise en charge actuellement par le client, Adobe recommande de définir la version HDCP sur `1.0`. Cela permet de s&#39;assurer que votre configuration est correctement formatée et est cohérente sémantiquement à l&#39;avenir lorsque la vérification de version HDCP est prise en charge. Le fragment de code suivant illustre une configuration avec cette valeur HDCP.

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

* **Q.** Les contraintes de pixels RBOP *sont-elles distinctes ou basées sur la plage ?* **A.** Les contraintes de pixels RBOP sont basées sur la plage. Chaque nombre de pixels définit les exigences pour tous les nombres de pixels inférieurs ou égaux au nombre donné ou jusqu’au plus grand nombre inférieur à cette valeur si plusieurs contraintes de pixels existent. En d’autres termes, les valeurs s’appliquent en tant que seuils maximaux pour chaque nombre vertical de pixels.

   Supposons qu’un flux MBR avec des résolutions verticales de 240, 480, 600, 720 et 1080 soit transmis à votre lecteur avec les paramètres RBOP suivants.

   **Paramètres de stratégie RBOP :**

   * 720P - HDCP requis
   * 480P - No OP
   Les règles suivantes seront appliquées à chaque variante.

   **Flux :**

   * 240, 480 : Les deux sont &lt;= 480 ; aucun OP n&#39;est requis et les flux se chargent avec ou sans HDCP présent.
   * 600, 720 : Tous deux sont &lt;= 720 ; HDCP est requis pour la lecture
   * 1080 : > 720 ; le flux est répertorié en bloc (erreur renvoyée) car il n’est pas trouvé dans les règles ci-dessus.


* **Q.** Sur certains appareils Android, les restrictions de nombre de pixels que j’ai définies ne sont pas appliquées exactement comme définies. Que se passe-t-il ?

   **R.** Certains périphériques Android ont des tailles d’image de rapports légèrement supérieures à la taille normale. Pour remédier à cette situation, ajustez les tailles des images ( `maxPixel` et `pixelCount` paramètres) à la hausse de 20 pixels. Par exemple, réglez les paramètres de taille d’image vers le haut, à partir de :

   ```
   { 
       "maxPixel":  
   
<b>800</b>,&quot;pixelConstraints&quot; : [{ &quot;pixelCount&quot;:\
<b>532</b>, &quot;digital&quot; : [{&quot;output&quot;: &quot;REQUIRED&quot;, &quot;hdcp&quot;:{&quot;major&quot; : 1, &quot;mineur&quot; : 0}}],&quot;analog&quot; : {&quot;output&quot;: &quot;REQUIRED&quot;}},...

```
to: 
```
{&quot;maxPixel&quot;:\
<b>820</b>,&quot;pixelConstraints&quot; : [{ &quot;pixelCount&quot;:\
<b>552</b>, &quot;digital&quot; : [{&quot;output&quot;: &quot;REQUIRED&quot;, &quot;hdcp&quot;:{&quot;major&quot; : 1, &quot;mineur&quot; : 0}}],&quot;analog&quot; : {&quot;output&quot;: &quot;REQUIRED&quot;}},...

```
throughout, for all instances of `maxPixel` and `pixelCount`.

