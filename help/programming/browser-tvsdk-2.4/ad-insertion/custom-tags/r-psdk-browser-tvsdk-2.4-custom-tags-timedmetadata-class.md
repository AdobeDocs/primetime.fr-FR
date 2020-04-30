---
description: Lorsque le navigateur TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter la balise et de l’exposer en tant qu’objet TimedMetadata.
seo-description: Lorsque le navigateur TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter la balise et de l’exposer en tant qu’objet TimedMetadata.
seo-title: Classe de métadonnées minutées
title: Classe de métadonnées minutées
uuid: 3f276618-5f61-4b41-bd2d-78e7f32178d9
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Classe de métadonnées minutées{#timed-metadata-class}

Lorsque le navigateur TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter la balise et de l’exposer en tant qu’objet TimedMetadata.

La `TimedMetadata` classe fournit les éléments suivants :

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
   <td colname="col2"> <p>Voici les types de métadonnées minutées : 
     <ul id="ul_E79C375A54C64BF09A927EE8983E98E3"> 
      <li id="li_F1907521CDBE47E282A87AF0A7A1477A">BALISE : les métadonnées minutées ont été créées à partir d’une balise dans la liste de lecture/le manifeste. </li> 
      <li id="li_5B0C0B0F247144709F86E6654A5AB500">ID3 : les métadonnées minutées ont été créées à partir d’une balise ID3 dans le flux média. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>time </p> </td> 
   <td colname="col02"> <p>Nombre </p> </td> 
   <td colname="col2"> <p>Position de l’heure locale (millisecondes) par rapport au début du contenu principal où ces métadonnées temporisées sont présentes dans le flux. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>id </p> </td> 
   <td colname="col02"> <p>Chaîne </p> </td> 
   <td colname="col2"> <p>Identificateur unique des métadonnées temporisées. </p> <p>Est généralement extrait de l’attribut ID de balise/indice s’il est présent. Sinon, il s’agit d’une valeur aléatoire unique. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>name </p> </td> 
   <td colname="col02"> <p>Nombre </p> </td> 
   <td colname="col2"> <p>Nom des métadonnées temporisées. </p> <p>Si le type est TAG, la valeur représente le indice/nom de la balise. Si le type est ID3, la valeur est nulle. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>content </p> </td> 
   <td colname="col02"> <p>Chaîne </p> </td> 
   <td colname="col2"> <p>Contenu brut des métadonnées temporisées. </p> <p>Si le type est TAG, la valeur représente la liste d’attribut entière du repère/balise. Si le type id3 est utilisé, la valeur est nulle. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>metadata </p> </td> 
   <td colname="col02"> <p><span class="codeph"> Métadonnées</span> </p> </td> 
   <td colname="col2"> <p>Informations traitées/extraites de la liste de lecture/balise personnalisée manifest. </p> </td> 
  </tr> 
 </tbody> 
</table>

