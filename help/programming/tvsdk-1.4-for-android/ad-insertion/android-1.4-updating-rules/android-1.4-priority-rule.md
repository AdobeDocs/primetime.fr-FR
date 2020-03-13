---
description: La règle de priorité définit l’ordre de priorité des créatifs publicitaires qui seront sélectionnés pour la lecture à partir d’une réponse VAST/VMAP.
keywords: priority rule;creative selection rules
seo-description: La règle de priorité définit l’ordre de priorité des créatifs publicitaires qui seront sélectionnés pour la lecture à partir d’une réponse VAST/VMAP.
seo-title: Règles de priorité
title: Règles de priorité
uuid: 6aa5822a-a3c0-49b2-b25b-0308a784e405
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Règles de priorité{#priority-rules}

La règle de priorité définit l’ordre de priorité des créatifs publicitaires qui seront sélectionnés pour la lecture à partir d’une réponse VAST/VMAP.

**Tableau 1 : Une règle de priorité possède les attributs et valeurs possibles suivants :**

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
   <td><span class="codeph"> priorité</span></td> 
   <td><span class="codeph"> Tableau</span></td> 
   <td></td> 
   <td> Tableau de types mime minuscules qui définissent la priorité dans laquelle les créatifs source doivent être sélectionnés pour la lecture.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td><span class="codeph"> hôte</span></td> 
   <td>Actuellement, seul <span class="codeph"> l’hôte</span> est pris en charge. Cet attribut doit être présent lorsque <span class="codeph"> des correspondances</span> et des attributs de valeurs <span class="codeph"></span> sont définis.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> correspond à</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td><span class="codeph"> multiple</span></td> 
   <td>Valeurs possibles :
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span> - est égal à</li> 
     <li><span class="codeph"> ne</span> - pas égal à</li> 
     <li><span class="codeph"> co</span> - contient</li> 
     <li><span class="codeph"> nc</span> - non contient</li> 
     <li><span class="codeph"> sw</span> -  avec</li> 
     <li><span class="codeph"> ew</span> - se termine par</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td><span class="codeph"> priorité</span></td> 
   <td>La valeur doit toujours être <span class="codeph"> prioritaire</span></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> valeurs</span></td> 
   <td><span class="codeph"> Tableau</span></td> 
   <td></td> 
   <td> <p>TVSDK utilisera l’attribut <span class="codeph"> correspond</span> sur l’élément <span class="codeph"></span> du créatif source et fera correspondre les valeurs définies dans ce tableau.</p> </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> stream</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td></td> 
   <td> <p>La valeur peut être <span class="codeph"> vod</span> ou <span class="codeph"> live</span></p> </td> 
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

