---
description: Lorsque TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter et d’exposer la balise sous la forme d’un objet TimedMetadata.
seo-description: Lorsque TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter et d’exposer la balise sous la forme d’un objet TimedMetadata.
seo-title: Classe de métadonnées minutées
title: Classe de métadonnées minutées
uuid: c7b1c1d7-48b3-43c7-aa21-f800d894976d
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---


# Classe de métadonnées minutées {#timed-metadata-class}

Lorsque TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter et d’exposer la balise sous la forme d’un objet TimedMetadata.

La classe fournit les éléments suivants :

<table id="table_FFC56AC5B1E04DA99C9309C0223ABA90"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b> Propriété </b></th> 
   <th colname="col02" class="entry"> <b> Type </b></th> 
   <th colname="col2" class="entry"> <b> Description </b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> id </span> </td> 
   <td colname="col02"> long </td> 
   <td colname="col2"> <p>Identificateur unique des métadonnées temporisées. </p> <p>Cette valeur est généralement extraite de l’attribut ID de balise/indice. Sinon, une valeur aléatoire unique est fournie. Utilisez <span class="codeph"> getId </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> metadata </span> </td> 
   <td colname="col02"> Métadonnées </td> 
   <td colname="col2"> <p>Informations traitées/extraites de la liste de lecture/balise personnalisée manifest. Utilisez <span class="codeph"> getMetadata </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> name </span> </td> 
   <td colname="col02"> Chaîne </td> 
   <td colname="col2"> <p>Nom des métadonnées temporisées. Si le type est <span class="codeph"> TAG </span>, la valeur représente le nom de la balise/indice. Si le type est <span class="codeph"> ID3 </span>, il est nul. Utilisez <span class="codeph"> getName </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> time </span> </td> 
   <td colname="col02"> long </td> 
   <td colname="col2"> <p>Position temporelle, en millisecondes, par rapport au début du contenu principal où ces métadonnées temporisées sont présentes dans le flux. Utilisez <span class="codeph"> getTime </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> type </span> </td> 
   <td colname="col02"> Type </td> 
   <td colname="col2"> <p>Type des métadonnées temporisées. Utilisez <span class="codeph"> getType </span>. 
     <ul id="ul_70FBFB33E9F846D8B38592560CCE9560"> 
      <li id="li_739D30561BFB4D9B97DF212E4880BA2C">BALISE : indique que les métadonnées minutées ont été créées à partir d’une balise dans la liste de lecture/manifeste. </li> 
      <li id="li_E785E1DEF1CC4D9DBE7764E5D05EFAFC">ID3 - indique que les métadonnées minutées ont été créées à partir d’une balise ID3 dans le flux média. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_737CC47997F74F80A3C5C6171ADE120E"></a>-->

Souvenez-vous des points suivants :

* TVSDK extrait automatiquement la liste d’attributs en paires clé-valeur et stocke les attributs dans la propriété metadata.

   >[!TIP]
   >
   >Les données complexes contenues dans les balises personnalisées du manifeste, telles que les chaînes contenant des caractères spéciaux, doivent être placées entre guillemets. Par exemple :
   >
   >
   ```
   >#EXT-CUSTOM-TAG:type=SpliceOut,ID=1,time=71819.7222,duration=30.0,url= 
   >"www.example.com:8090?parameter1=xyz&parameter2=abc"
   >```

* Si l’extraction échoue en raison d’un format de balise personnalisé, la propriété metadata est vide et votre application doit extraire les informations réelles. Dans ce cas, aucune erreur n’est générée.

<table id="table_1BAE98BF23F641A3A5709EBE37B327F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> <b>Elément </b></th> 
   <th colname="col2" class="entry"> <b>Description</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public enum Type {TAG, ID3} </span> </td> 
   <td colname="col2"> <p>Types possibles pour les métadonnées temporisées. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public TimedMetadata (type, long time, long id, nom de chaîne, métadonnées); </span> </td> 
   <td colname="col2"> <p>Constructeur par défaut (heure correspond à l’heure locale du flux). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public long getTime(); </span> </td> 
   <td colname="col2"> <p>Position temporelle, par rapport au début du contenu principal, où ces métadonnées ont été insérées dans le flux. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public Metadata getMetadata(); </span> </td> 
   <td colname="col2"> <p>Métadonnées insérées dans le flux. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public Type getType(); </span> </td> 
   <td colname="col2"> <p>Renvoie le type des métadonnées minutées. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public long getId(); </span> </td> 
   <td colname="col2"> <p>Renvoie l’ID extrait des attributs de balise/indice. Sinon, une valeur aléatoire unique est fournie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public String getName(); </span> </td> 
   <td colname="col2"> <p>Renvoie le nom du repère, qui est généralement le nom de balise HLS. </p> </td> 
  </tr> 
 </tbody> 
</table>