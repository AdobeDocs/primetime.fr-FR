---
description: La règle de normalisation définit une transformation d’URL à appliquer à une URL de création source obtenue à partir d’une réponse VAST/VMAP.
keywords: normalize rule;creative selection rules
seo-description: La règle de normalisation définit une transformation d’URL à appliquer à une URL de création source obtenue à partir d’une réponse VAST/VMAP.
seo-title: Normalisation des règles
title: Normalisation des règles
uuid: ae0364d2-23e2-48d6-b9b6-869cd163080d
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# Normaliser les règles {#normalize-rules}

La règle de normalisation définit une transformation d’URL à appliquer à une URL de création source obtenue à partir d’une réponse VAST/VMAP.

## La règle de normalisation comporte les attributs et valeurs possibles suivants :

<table id="table_ljp_tgx_hz">  
 <thead> 
  <tr> 
   <th class="entry"> Clé</th> 
   <th class="entry"> Type</th> 
   <th class="entry"> Valeurs</th> 
   <th class="entry"> Description</th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td><span class="codeph"> normaliser</span></td> 
   <td>La valeur doit toujours être <span class="codeph"> normaliser</span>.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td><span class="codeph"> hôte</span></td> 
   <td>Actuellement, seul <span class="codeph"> hôte</span> est pris en charge. Cet attribut doit être présent lorsque les attributs <span class="codeph"> correspondent à </span> et <span class="codeph"> valeurs</span> sont définis.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> correspond</span></td> 
   <td></td> 
   <td></td> 
   <td>Valeurs possibles :
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span> - est égal à</li> 
     <li><span class="codeph"> ne</span> - pas égal à</li> 
     <li><span class="codeph"> co</span> - contient</li> 
     <li><span class="codeph"> nc</span> - ne contient pas</li> 
     <li><span class="codeph"> sw</span> - débuts avec</li> 
     <li><span class="codeph"> ew</span> - se termine par</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> values</span></td> 
   <td><span class="codeph"> Tableau</span></td> 
   <td></td> 
   <td>TVSDK utilisera l’attribut <span class="codeph"> correspond</span> sur l’élément <span class="codeph"> </span> du créatif source et fera correspondre les valeurs définies dans ce tableau.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rechercher</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> Expression régulière à appliquer sur l’URL de création source à faire correspondre.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> remplacer</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> Expression régulière à appliquer sur l’URL de création source à remplacer en fonction de la correspondance.</td> 
  </tr> 
 </tbody> 
</table>

```
{
    "ads": {
        "rules": {
            "default": [
                {
                ...
                }
                {
                    "
<b>type</b>": "
<b>normalize</b>",
                    "
<b>item</b>": "host",
                    "
<b>matches</b>": "ew",
                    "
<b>values</b>": [
                        "redirector.gvt1.com"
                    ],
                    "
<b>find</b>": "videoplayback/(.*?)/expire/.*?/(.*?)/signature/.*?/",
                    "
<b>replace</b>": "videoplayback/$1/expire//$2/signature//"
                }                
            ]
        }
    }
}
```

