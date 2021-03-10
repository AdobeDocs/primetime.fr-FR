---
description: La règle de priorité définit l’ordre de priorité des créatifs publicitaires qui seront sélectionnés pour la lecture à partir d’une réponse VAST/VMAP.
keywords: règle de priorité ; règles de sélection créative
title: Règles de priorité
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# Règles de priorité {#priority-rules}

La règle de priorité définit l’ordre de priorité des créatifs publicitaires qui seront sélectionnés pour la lecture à partir d’une réponse VAST/VMAP.

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
   <td><span class="codeph"> priority</span></td> 
   <td><span class="codeph"> Tableau</span></td> 
   <td></td> 
   <td> Tableau de types minuscules mime qui définissent la priorité dans laquelle les créatifs source doivent être sélectionnés pour la lecture.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td><span class="codeph"> hôte</span></td> 
   <td>Actuellement, seul <span class="codeph"> hôte</span> est pris en charge. Cet attribut doit être présent lorsque les attributs <span class="codeph"> correspondent à </span> et <span class="codeph"> valeurs</span> sont définis.</td> 
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
     <li><span class="codeph"> nc</span> - ne contient pas</li> 
     <li><span class="codeph"> sw</span> - débuts avec</li> 
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
   <td> <p>TVSDK utilisera l’attribut <span class="codeph"> correspond</span> sur l’élément <span class="codeph"> </span> du créatif source et fera correspondre les valeurs définies dans ce tableau.</p> </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> stream</span></td> 
   <td><span class="codeph"> Chaîne</span></td> 
   <td></td> 
   <td> <p>La valeur peut être <span class="codeph"> vod</span> ou <span class="codeph"> live</span>.</p> </td> 
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
