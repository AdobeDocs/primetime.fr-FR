---
description: Lorsque TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter la balise et de l’exposer sous la forme d’un objet TimedMetadata.
title: Classe de métadonnées minutées
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# Classe de métadonnées minutées{#timed-metadata-class}

Lorsque TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter la balise et de l’exposer sous la forme d’un objet TimedMetadata.

La classe fournit les éléments suivants :

<table id="table_FFC56AC5B1E04DA99C9309C0223ABA90"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Propriété </th> 
   <th colname="col02" class="entry"> Type </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> id  </span> </td> 
   <td colname="col02"> long </td> 
   <td colname="col2"> Identificateur unique des métadonnées temporisées. Cette valeur est généralement extraite de l’attribut ID de balise/indice. Sinon, une valeur aléatoire unique est fournie. Utilisez <span class="codeph"> getId </span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> metadata  </span> </td> 
   <td colname="col02"> Métadonnées </td> 
   <td colname="col2"> Informations traitées/extraites de la liste de lecture/balise personnalisée manifest. Utilisez <span class="codeph"> getMetadata </span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> name </span> </td> 
   <td colname="col02"> Chaîne </td> 
   <td colname="col2"> Nom des métadonnées temporisées. Si le type est <span class="codeph"> TAG </span>, la valeur représente le nom de la balise/indice. Si le type est <span class="codeph"> ID3 </span>, il est nul. Utilisez <span class="codeph"> getName </span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> time  </span> </td> 
   <td colname="col02"> long </td> 
   <td colname="col2"> Position temporelle, en millisecondes, par rapport au début du contenu principal où ces métadonnées temporisées sont présentes dans le flux. Utilisez <span class="codeph"> getTime </span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> type  </span> </td> 
   <td colname="col02"> Type </td> 
   <td colname="col2"> Type des métadonnées temporisées. Utilisez <span class="codeph"> getType </span>. 
    <ul id="ul_70FBFB33E9F846D8B38592560CCE9560"> 
     <li id="li_739D30561BFB4D9B97DF212E4880BA2C">BALISE : indique que les métadonnées minutées ont été créées à partir d’une balise dans la liste de lecture/manifeste. </li> 
     <li id="li_E785E1DEF1CC4D9DBE7764E5D05EFAFC">ID3 - indique que les métadonnées minutées ont été créées à partir d’une balise ID3 dans le flux média. </li> 
    </ul> </td> 
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
   >#EXT-CUSTOM-TAG:type=SpliceOut,ID=1,time=71819.7222,duration=30.0, 
   >url="www.example.com:8090?parameter1=xyz&parameter2=abc"
   >```

* Si l’extraction échoue en raison d’un format de balise personnalisé, la propriété metadata est vide et votre application doit extraire les informations réelles. Aucune erreur n’est générée dans ce cas.

| Elément | Description |
|---|---|
| `public enum Type { TAG, ID3}` | Types possibles pour les métadonnées temporisées. |
| `public TimedMetadata(Type type, long time, long id, String name, Metadata metadata);` | Constructeur par défaut (heure correspond à l’heure locale du flux). |
| `public long getTime();` | Position temporelle, par rapport au début du contenu principal, où ces métadonnées ont été insérées dans le flux. |
| `public Metadata getMetadata();` | Métadonnées insérées dans le flux. |
| `public Type getType();` | Renvoie le type des métadonnées minutées. |
| `public long getId();` | Renvoie l’ID extrait des attributs de balise/indice. Sinon, une valeur aléatoire unique est fournie. |
| `public String getName();` | Renvoie le nom du repère, qui est généralement le nom de balise HLS. |

