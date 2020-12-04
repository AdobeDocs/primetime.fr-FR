---
description: La qualité de service (QoS) offre une vue détaillée sur les performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.
seo-description: La qualité de service (QoS) offre une vue détaillée sur les performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.
seo-title: Suivi au niveau du fragment à l’aide des informations de chargement
title: Suivi au niveau du fragment à l’aide des informations de chargement
uuid: a6572823-d525-4ce0-806a-3feb20678cb0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# Suivi au niveau du fragment à l’aide des informations de chargement{#track-at-the-fragment-level-using-load-information}

La qualité de service (QoS) offre une vue détaillée sur les performances du moteur vidéo. TVSDK fournit des statistiques détaillées sur la lecture, la mise en mémoire tampon et les périphériques.

TVSDK fournit également des informations sur les ressources téléchargées suivantes :

1. Fichiers de liste de lecture/manifestes
1. Fragments de fichier
1. Suivi des informations relatives aux fichiers

   Vous pouvez lire les informations de qualité de service (QoS) sur les ressources téléchargées, telles que les fragments et les pistes, à partir de la classe `LoadInfo`.

1. Mettez en oeuvre l’écouteur de événement de rappel `onLoadInfo`.
1. Enregistrez l’écouteur de événement, que TVSDK appelle chaque fois qu’un fragment est téléchargé.
1. Lisez les données présentant un intérêt à partir du paramètre `LoadInfo` transmis au rappel.

   <table id="table_06BD536A23AB4A73B510998426BAE143"> 
    <thead> 
      <tr> 
      <th colname="col01" class="entry"> Propriété </th> 
      <th colname="col1" class="entry"> Type </th> 
      <th colname="col2" class="entry"> Description </th> 
      </tr> 
    </thead>
    <tbody> 
      <tr> 
      <td colname="col01"> <span class="codeph"> downloadDuration  </span> </td> 
      <td colname="col1"> <span class="codeph"> long  </span> </td> 
      <td colname="col2"> <p>Durée du téléchargement en millisecondes. </p> <p>TVSDK ne fait pas la distinction entre le temps nécessaire au client pour se connecter au serveur et le temps nécessaire pour télécharger le fragment complet. Par exemple, si le téléchargement d’un segment de 10 Mo prend 8 secondes, TVSDK fournit ces informations, mais ne vous indique pas qu’il a fallu 4 secondes avant le premier octet et 4 secondes supplémentaires pour télécharger l’intégralité du fragment. </p> </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> mediaDuration  </span> </td> 
      <td colname="col1"> <span class="codeph"> long  </span> </td> 
      <td colname="col2"> Durée du média des fragments téléchargés en millisecondes. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> periodIndex  </span> </td> 
      <td colname="col1"> <span class="codeph"> int  </span> </td> 
      <td colname="col2"> Index de période de chronologie associé à la ressource téléchargée. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> taille  </span> </td> 
      <td colname="col1"> <span class="codeph"> long  </span> </td> 
      <td colname="col2"> Taille de la ressource téléchargée en octets. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackIndex  </span> </td> 
      <td colname="col1"> <span class="codeph"> int  </span> </td> 
      <td colname="col2"> L'index de la voie correspondante, s'il est connu ; sinon, 0. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackName  </span> </td> 
      <td colname="col1"> <span class="codeph"> Chaîne  </span> </td> 
      <td colname="col2"> Le nom de la voie correspondante, s'il est connu ; sinon, nul. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackType  </span> </td> 
      <td colname="col1"> <span class="codeph"> Chaîne  </span> </td> 
      <td colname="col2"> le type de la voie correspondante, s'il est connu ; sinon, nul. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> type  </span> </td> 
      <td colname="col1"> <span class="codeph"> Chaîne  </span> </td> 
      <td colname="col2"> Contenu téléchargé par TVSDK. L'un des éléments suivants : 
      <ul id="ul_9C3BDEBD878544DA95C7FF81114F9B5C"> 
      <li id="li_A093552B492A44FD8B30785E465F6886">MANIFEST - Liste de lecture/manifeste </li> 
      <li id="li_DEF9AC71AA564F9BB4C5D4E834432EE5">FRAGMENT - Un fragment </li> 
      <li id="li_57821F47B6F04CD38570BCE6447A01B8">TRACK : fragment associé à une piste spécifique </li> 
      </ul> Il peut parfois être impossible de détecter le type de ressource. Si cela se produit, FILE est renvoyé. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> url  </span> </td> 
      <td colname="col1"> <span class="codeph"> Chaîne  </span> </td> 
      <td colname="col2"> URL pointant vers la ressource téléchargée. </td> 
      </tr> 
    </tbody> 
   </table>
