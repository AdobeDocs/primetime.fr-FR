---
description: Questions fréquentes sur l’utilisation de la protection de sortie basée sur la résolution.
seo-description: Questions fréquentes sur l’utilisation de la protection de sortie basée sur la résolution.
seo-title: FAQ sur RBOP
title: FAQ sur RBOP
uuid: 7dcd337c-369a-474c-8768-409c48b5cee5
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# FAQ sur RBOP {#rbop-faq}

Questions fréquentes sur l’utilisation de la protection de sortie basée sur la résolution.

* **Q.** *Lors de la définition d’une exigence de sortie numérique pour une contrainte de pixels, j’obtiens des erreurs d’analyse/de formatage lorsque je quitte la version HDCP, mais je n’ai aucune exigence HDCP. Comment dois-je configurer mes exigences en matière de sortie numérique dans ce cas ?* **A.** La vérification de version HDCP n’étant actuellement pas prise en charge par le client, Adobe recommande de définir la version HDCP sur `1.0`. Cela vous permettra de vous assurer que votre configuration est correctement formatée et est cohérente sémantiquement dans le futur lorsque la vérification de version HDCP est prise en charge. Le fragment de code suivant illustre une configuration avec cette valeur HDCP.

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

* **Q.** *Les contraintes de pixels RBOP sont-elles distinctes ou basées sur une plage ?* **A.** Les contraintes de pixels RBOP sont basées sur la plage. Chaque nombre de pixels définit les exigences pour tous les nombres de pixels inférieurs ou égaux au nombre donné ou jusqu’au plus grand nombre inférieur à cette valeur si plusieurs contraintes de pixels existent. En d’autres termes, les valeurs s’appliquent comme seuils maximaux pour chaque nombre de pixels vertical.

   Supposons qu’un flux MBR avec des résolutions verticales de 240, 480, 600, 720 et 1080 soit transmis à votre lecteur avec les paramètres RBOP suivants.

   **Paramètres de stratégie RBOP :**

   * 720P - HDCP requis
   * 480P - No OP
   Les règles suivantes seront appliquées à chaque variante.

   **Flux :**

   * 240, 480 : Tous deux sont &lt;= 480; aucun OP ne doit être requis et les flux se chargent avec ou sans HDCP présent.
   * 600, 720 : Tous deux sont &lt;= 720; HDCP est requis pour la lecture
   * 1080 : > 720; le flux est (erreur renvoyée), car il est introuvable dans les règles ci-dessus.


* **Q.** Sur certains appareils Android, les restrictions de nombre de pixels que j’ai définies ne sont pas appliquées exactement comme définies. Que se passe-t-il ?

   **A.** Certains périphériques Android sont  de tailles d’image légèrement supérieures à la taille normale. Pour remédier à cette situation, ajustez les tailles des images ( `maxPixel` et `pixelCount` paramètres) vers le haut de 20 pixels. Par exemple, réglez les paramètres de taille d’image vers le haut à partir de :

   ```
   { 
       "maxPixel":  
   
<b>800</b>,&quot;pixelConstraints&quot; : [{ &quot;pixelCount&quot; :\
<b>532</b>, &quot;digital&quot;: [{&quot;output&quot; : &quot;REQUIRED&quot;, &quot;hdcp&quot;:{&quot;major&quot;: 1,&quot;mineur&quot; : 0}}],&quot;analog&quot; : {&quot;output&quot; : &quot;REQUIRED&quot;},...

```
to: 
```
{&quot;maxPixel&quot; :\
<b>820</b>,&quot;pixelConstraints&quot; : [{ &quot;pixelCount&quot; :\
<b>552</b>, &quot;digital&quot;: [{&quot;output&quot; : &quot;REQUIRED&quot;, &quot;hdcp&quot;:{&quot;major&quot;: 1,&quot;mineur&quot; : 0}}],&quot;analog&quot; : {&quot;output&quot; : &quot;REQUIRED&quot;},...

```
throughout, for all instances of `maxPixel` and `pixelCount`.

