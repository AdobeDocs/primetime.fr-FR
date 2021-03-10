---
description: La règle de normalisation définit une transformation d’URL à appliquer à une URL de création source obtenue à partir d’une réponse VAST/VMAP.
keywords: normaliser la règle ; règles de sélection créative
title: Normalisation des règles
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---


# Normaliser les règles {#normalize-rules}

La règle de normalisation définit une transformation d’URL à appliquer à une URL de création source obtenue à partir d’une réponse VAST/VMAP.

<table id="table_ljp_tgx_hz">  
 <thead> 
  <tr> 
   <th class="entry"><b>Clé</b></th> 
   <th class="entry"><b>Type</b></th> 
   <th class="entry"><b>Valeurs</b></th> 
   <th class="entry"><b>Description</b></th>
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
