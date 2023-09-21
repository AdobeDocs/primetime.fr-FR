---
description: La règle de priorité définit l’ordre de priorité des créatifs publicitaires qui seront sélectionnés pour la lecture à partir d’une réponse VAST/VMAP.
keywords: règle de priorité, règles de sélection créative
title: Règles de priorité
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

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
   <td><span class="codeph"> priority</span></td> 
   <td><span class="codeph"> Tableau</span></td> 
   <td></td> 
   <td> Tableau de types MIME minuscules qui définissent la priorité dans laquelle les créatifs sources doivent être sélectionnés pour la lecture.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td><span class="codeph"> hôte</span></td> 
   <td>Actuellement uniquement <span class="codeph"> hôte</span> est prise en charge. Cet attribut doit être présent lorsque <span class="codeph"> correspond à</span> et <span class="codeph"> values</span> Les attributs sont définis.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> correspond à</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td><span class="codeph"> multiple</span></td> 
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
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td><span class="codeph"> priority</span></td> 
   <td>La valeur doit toujours être <span class="codeph"> priority</span></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> values</span></td> 
   <td><span class="codeph"> Tableau</span></td> 
   <td></td> 
   <td> <p>TVSDK utilisera la variable <span class="codeph"> correspond à</span> sur l’attribut <span class="codeph"> item</span> du créatif source et faites correspondre les valeurs définies dans ce tableau</p> </td> 
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
