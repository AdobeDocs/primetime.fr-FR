---
description: Lorsque TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter la balise et de l’exposer sous la forme d’un objet PTTimedMetadata.
title: Classe de métadonnées minutée
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Classe de métadonnées minutée {#timed-metadata-class}

Lorsque TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter la balise et de l’exposer sous la forme d’un objet PTTimedMetadata.

La classe fournit les éléments suivants :

<table id="table_FFC56AC5B1E04DA99C9309C0223ABA90"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>Propriété</b></th> 
   <th colname="col02" class="entry"><b>Type</b> </th> 
   <th colname="col2" class="entry"><b>Description</b></th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> metadataId</span> </td> 
   <td colname="col02"><span class="codeph"> NSString</span> </td> 
   <td colname="col2"> Identifiant unique des métadonnées minutées. Cette valeur est généralement extraite de l’attribut ID de repère/de balise. Dans le cas contraire, une valeur aléatoire unique est fournie. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> name</span> </td> 
   <td colname="col02"><span class="codeph"> NSString</span></td> 
   <td colname="col2"> Nom des métadonnées minutées. Si le type est <span class="codeph"> BALISE</span>, la valeur représente le nom de repère/balise. Si le type est <span class="codeph"> ID3</span>, elle est nulle. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> time</span> </td> 
   <td colname="col02"><span class="codeph"> CMTime</span></td> 
   <td colname="col2"> Position, en millisecondes, par rapport au début du contenu principal où ces métadonnées minutées sont présentes dans le flux. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> type</span> </td> 
   <td colname="col02"> <span class="codeph"> PTTimedMetadataType</span></td> 
   <td colname="col2">Type des métadonnées minutées. 
    <ul id="ul_70FBFB33E9F846D8B38592560CCE9560"> 
     <li id="li_739D30561BFB4D9B97DF212E4880BA2C">BALISE : indique que les métadonnées minutées ont été créées à partir d’une balise dans la liste de lecture/le manifeste. </li> 
     <li id="li_E785E1DEF1CC4D9DBE7764E5D05EFAFC">ID3 : indique que les métadonnées minutées ont été créées à partir d’une balise ID3 dans le flux multimédia. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_737CC47997F74F80A3C5C6171ADE120E"></a>-->

Gardez à l’esprit les éléments suivants :

* TVSDK extrait automatiquement la liste d’attributs en paires clé-valeur et stocke les attributs dans la propriété de métadonnées.

  >[!TIP]
  >
  >Les données complexes des balises personnalisées du manifeste, telles que les chaînes contenant des caractères spéciaux, doivent être placées entre guillemets. Par exemple :
  >
  >```
  >#EXT-CUSTOM-TAG:type=SpliceOut,ID=1,time=71819.7222,duration=30.0,url=
  >"www.example.com:8090?parameter1=xyz&parameter2=abc"
  >```
  >

* Si l’extraction échoue en raison d’un format de balise personnalisé, la propriété content contient toujours les données brutes de la balise, qui sont la chaîne située après le signe deux-points. Dans ce cas, aucune erreur n’est générée.

| **Élément** | **Description** |
|---|---|
| BALISE, ID3 | Types possibles des métadonnées minutées. |
| `@property (nonatomic, assign) CMTime time` | Position temporelle, par rapport au début du contenu principal, où ces métadonnées ont été insérées dans le flux. |
| `@property (nonatomic, assign) PTTimedMetadataType type` | Renvoie le type des métadonnées minutées. |
| `@property (nonatomic, retain) NSString *metadataId` | Renvoie l’identifiant extrait des attributs de repère/balise. Dans le cas contraire, une valeur aléatoire unique est fournie. |
| `@property (nonatomic, retain) NSString *name` | Renvoie le nom du repère, qui est généralement le nom de la balise HLS. |
