---
description: Lorsque le TVSDK du navigateur détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter la balise et de l’exposer en tant qu’objet TimedMetadata.
title: Classe de métadonnées minutée
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Classe de métadonnées minutée{#timed-metadata-class}

Lorsque le TVSDK du navigateur détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter la balise et de l’exposer en tant qu’objet TimedMetadata.

La variable `TimedMetadata` fournit les éléments suivants :

<table id="table_5827A0626EDC45F68DC3E7644F3EFF69"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Propriété </th> 
   <th colname="col02" class="entry"> Type </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>type </p> </td> 
   <td colname="col02"> <p><span class="codeph"> TimedMetadataType</span> </p> </td> 
   <td colname="col2"> <p>Voici les types de métadonnées minutés : 
     <ul id="ul_E79C375A54C64BF09A927EE8983E98E3"> 
      <li id="li_F1907521CDBE47E282A87AF0A7A1477A">BALISE : les métadonnées minutées ont été créées à partir d’une balise dans la liste de lecture/le manifeste. </li> 
      <li id="li_5B0C0B0F247144709F86E6654A5AB500">ID3 : les métadonnées minutées ont été créées à partir d’une balise ID3 dans le flux multimédia. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>time </p> </td> 
   <td colname="col02"> <p>Nombre </p> </td> 
   <td colname="col2"> <p>Position de l’heure locale (millisecondes) par rapport au début du contenu principal où ces métadonnées minutées sont présentes dans le flux. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>id </p> </td> 
   <td colname="col02"> <p>Chaîne </p> </td> 
   <td colname="col2"> <p>Identifiant unique des métadonnées minutées. </p> <p>Est généralement extrait de l’attribut ID de repère/de balise s’il est présent. Sinon, il s’agit d’une valeur aléatoire unique. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>name </p> </td> 
   <td colname="col02"> <p>Nombre </p> </td> 
   <td colname="col2"> <p>Nom des métadonnées minutées. </p> <p>Si le type est TAG, la valeur représente le nom de repère/balise. Si le type est ID3, la valeur est nulle. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>content </p> </td> 
   <td colname="col02"> <p>Chaîne </p> </td> 
   <td colname="col2"> <p>Contenu brut des métadonnées minutées. </p> <p>Si le type est TAG, la valeur représente la liste complète des attributs du repère/de la balise. Si le type ID3 est utilisé, la valeur est nulle. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>metadata </p> </td> 
   <td colname="col02"> <p><span class="codeph"> Métadonnées</span> </p> </td> 
   <td colname="col2"> <p>Les informations traitées/extraites de la balise personnalisée playlist/manifest. </p> </td> 
  </tr> 
 </tbody> 
</table>
