---
description: La règle de normalisation définit une transformation d’URL à appliquer à une URL créative source obtenue à partir d’une réponse VAST/VMAP.
keywords: règle de normalisation;règles de sélection créative
title: Normalisation des règles
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# Normalisation des règles{#normalize-rules}

La règle de normalisation définit une transformation d’URL à appliquer à une URL créative source obtenue à partir d’une réponse VAST/VMAP.

**Tableau 2 : La règle de normalisation possède les attributs suivants et les valeurs possibles :**

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
   <td>Actuellement uniquement <span class="codeph"> hôte</span> est prise en charge. Cet attribut doit être présent lorsque <span class="codeph"> correspond à</span> et <span class="codeph"> values</span> Les attributs sont définis.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> correspond à</span></td> 
   <td></td> 
   <td></td> 
   <td>Valeurs possibles :
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span> - est égal à</li> 
     <li><span class="codeph"> ne</span> - différent de</li> 
     <li><span class="codeph"> co</span> - contient</li> 
     <li><span class="codeph"> nc</span> - ne contient pas</li> 
     <li><span class="codeph"> sw</span> - commence par</li> 
     <li><span class="codeph"> ew</span> - se termine par</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> values</span></td> 
   <td><span class="codeph"> Tableau</span></td> 
   <td></td> 
   <td>TVSDK utilisera la variable <span class="codeph"> correspond à</span> sur l’attribut <span class="codeph"> item</span> de la source créative et faites correspondre les valeurs définies dans ce tableau.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> find</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> Expression régulière à appliquer sur l’URL de création source à faire correspondre.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> replace</span></td> 
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
