---
description: Lorsque TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter la balise et de l’exposer sous la forme d’un objet PTTimedMetadata.
seo-description: Lorsque TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter la balise et de l’exposer sous la forme d’un objet PTTimedMetadata.
seo-title: Classe de métadonnées minutées
title: Classe de métadonnées minutées
uuid: d76b2a6b-2995-4559-b15d-82ded4c27eea
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '357'
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
   <td colname="col2"> Identificateur unique des métadonnées temporisées. Cette valeur est généralement extraite de l’attribut ID de balise/indice. Sinon, une valeur aléatoire unique est fournie. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> name</span> </td> 
   <td colname="col02"><span class="codeph"> NSString</span></td> 
   <td colname="col2"> Nom des métadonnées temporisées. Si le type est <span class="codeph"> TAG</span>, la valeur représente le nom de la balise/indice. Si le type est <span class="codeph"> ID3</span>, il est nul. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> time</span> </td> 
   <td colname="col02"><span class="codeph"> CMTime</span></td> 
   <td colname="col2"> Position temporelle, en millisecondes, par rapport au début du contenu principal où ces métadonnées temporisées sont présentes dans le flux. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> type</span> </td> 
   <td colname="col02"> <span class="codeph"> PTTimedMetadataType</span></td> 
   <td colname="col2">Type des métadonnées temporisées. 
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
   >#EXT-CUSTOM-TAG:type=SpliceOut,ID=1,time=71819.7222,duration=30.0,url=
   >"www.example.com:8090?parameter1=xyz&parameter2=abc"
   >```

* Si l’extraction échoue en raison d’un format de balise personnalisé, la propriété de contenu contient toujours les données brutes de la balise, c’est-à-dire la chaîne située après les deux-points. Aucune erreur n’est générée dans ce cas.

| **Elément** | **Description** |
|---|---|
| BALISE, ID3 | Types possibles pour les métadonnées temporisées. |
| `@property (nonatomic, assign) CMTime time` | Position temporelle, par rapport au début du contenu principal, où ces métadonnées ont été insérées dans le flux. |
| `@property (nonatomic, assign) PTTimedMetadataType type` | Renvoie le type des métadonnées minutées. |
| `@property (nonatomic, retain) NSString *metadataId` | Renvoie l’ID extrait des attributs de balise/indice. Sinon, une valeur aléatoire unique est fournie. |
| `@property (nonatomic, retain) NSString *name` | Renvoie le nom du repère, qui est généralement le nom de balise HLS. |