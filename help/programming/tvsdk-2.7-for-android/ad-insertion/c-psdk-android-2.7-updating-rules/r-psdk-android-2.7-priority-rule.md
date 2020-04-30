---
description: La règle de priorité définit l’ordre de priorité des créatifs publicitaires qui seront sélectionnés pour la lecture à partir d’une réponse VAST/VMAP.
keywords: priority rule;creative selection rules
seo-description: La règle de priorité définit l’ordre de priorité des créatifs publicitaires qui seront sélectionnés pour la lecture à partir d’une réponse VAST/VMAP.
seo-title: Règles de priorité
title: Règles de priorité
uuid: 4ca31dc7-9c5e-400c-9111-e7b6fc11a392
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Règles de priorité {#priority-rules}

La règle de priorité définit l’ordre de priorité des créatifs publicitaires qui seront sélectionnés pour la lecture à partir d’une réponse VAST/VMAP.

## Une règle Priorité comporte les attributs et valeurs possibles suivants :

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
   <td><span class="codeph"> priority</span></td> 
   <td><span class="codeph"> Tableau</span></td> 
   <td></td> 
   <td> Tableau de types minuscules mime qui définissent la priorité dans laquelle les créatifs source doivent être sélectionnés pour la lecture.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td><span class="codeph"> hôte</span></td> 
   <td>Actuellement, seul <span class="codeph"> l’hôte</span> est pris en charge. Cet attribut doit être présent lorsque des <span class="codeph"> correspondances</span> et des attributs de <span class="codeph"> valeurs</span> sont définis.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> correspond</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td><span class="codeph"> multiple</span></td> 
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
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td><span class="codeph"> priority</span></td> 
   <td>La valeur doit toujours être <span class="codeph"> prioritaire</span></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> values</span></td> 
   <td><span class="codeph"> Tableau</span></td> 
   <td></td> 
   <td> <p>TVSDK utilisera l’attribut <span class="codeph"> match</span> sur l’élément <span class="codeph"></span> de création source et fera une correspondance avec les valeurs définies dans ce tableau.</p> </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> stream</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td></td> 
   <td> <p>La valeur peut être <span class="codeph"> validée</span> ou <span class="codeph"> active</span></p> </td> 
  </tr> 
 </tbody> 
</table>

```
{
    "ads": {
        "rules": {
            "default": [
                {
                    "
<b>type</b>": "
<b>priority</b>",
                    "
<b>stream</b>": "vod",
                    "
<b>priority</b>": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "application/x-shockwave-flash",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    ...
                },
            ]
        }
    }
}
```

