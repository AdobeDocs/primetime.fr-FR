---
description: La règle de normalisation définit une transformation d’URL à appliquer à une URL de création source obtenue à partir d’une réponse VAST/VMAP.
keywords: normalize rule;creative selection rules
seo-description: La règle de normalisation définit une transformation d’URL à appliquer à une URL de création source obtenue à partir d’une réponse VAST/VMAP.
seo-title: Normalisation des règles
title: Normalisation des règles
uuid: b3ca2c8e-133a-4630-8109-17bf0a91843d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Normalisation des règles{#normalize-rules}

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
   <td>La valeur doit toujours être <span class="codeph"> normalisée</span>.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td><span class="codeph"> hôte</span></td> 
   <td>Actuellement, seul <span class="codeph"> l’hôte</span> est pris en charge. Cet attribut doit être présent lorsque des <span class="codeph"> correspondances</span> et des attributs de <span class="codeph"> valeurs</span> sont définis.</td> 
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
     <li><span class="codeph"> nc</span> - non contient</li> 
     <li><span class="codeph"> sw</span> - débuts avec</li> 
     <li><span class="codeph"> ew</span> - se termine par</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> values</span></td> 
   <td><span class="codeph"> Tableau</span></td> 
   <td></td> 
   <td>TVSDK utilisera l’attribut <span class="codeph"> correspond</span> sur l’élément <span class="codeph"></span> du créatif source et fera une correspondance avec les valeurs définies dans ce tableau.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rechercher</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> expression régulière à appliquer sur l’URL de création source à faire correspondre.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> remplacer</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> expression régulière à appliquer sur l’URL de création source à remplacer en fonction de la correspondance.</td> 
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

