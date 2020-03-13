---
description: Lorsque TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter la balise et de l’exposer sous la forme d’un objet PTTimedMetadata.
seo-description: Lorsque TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter la balise et de l’exposer sous la forme d’un objet PTTimedMetadata.
seo-title: Classe de métadonnées minutées
title: Classe de métadonnées minutées
uuid: d1ac6b0b-163f-4968-9160-0f60ff439c09
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Classe de métadonnées minutées{#timed-metadata-class}

Lorsque TVSDK détecte une balise abonnée dans la liste de lecture/le manifeste, le lecteur tente automatiquement de traiter la balise et de l’exposer sous la forme d’un objet PTTimedMetadata.

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
   <td colname="col1"> <span class="codeph"> metadataId</span> </td> 
   <td colname="col02"><span class="codeph"> NSString</span> </td> 
   <td colname="col2"> Identifiant unique des métadonnées temporisées. Cette valeur est généralement extraite de l’attribut indice/ID de balise. Sinon, une valeur aléatoire unique est fournie. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> name</span> </td> 
   <td colname="col02"><span class="codeph"> NSString</span></td> 
   <td colname="col2"> Nom des métadonnées minutées. Si le type est <span class="codeph"> BALISE</span>, la valeur représente le nom du repère/de la balise. Si le type est <span class="codeph"> ID3</span>, il est nul. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> time</span> </td> 
   <td colname="col02"><span class="codeph"> CMTime</span></td> 
   <td colname="col2"> Position temporelle, en millisecondes, par rapport à la  du contenu principal où sont présentes ces métadonnées minutées dans le flux. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> type</span> </td> 
   <td colname="col02"> <span class="codeph"> PTTimedMetadataType</span></td> 
   <td colname="col2">Type des métadonnées temporisées. 
    <ul id="ul_70FBFB33E9F846D8B38592560CCE9560"> 
     <li id="li_739D30561BFB4D9B97DF212E4880BA2C">BALISE : indique que les métadonnées minutées ont été créées à partir d’une balise dans la liste de lecture/le manifeste. </li> 
     <li id="li_E785E1DEF1CC4D9DBE7764E5D05EFAFC">ID3 : indique que les métadonnées minutées ont été créées à partir d’une balise ID3 dans le flux média. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_737CC47997F74F80A3C5C6171ADE120E"></a>-->

Tenez compte des points suivants :

* TVSDK extrait automatiquement le d’attributs en paires clé-valeur et stocke les attributs dans la propriété de métadonnées.

   >[!TIP]
   >
   >Les données complexes contenues dans les balises personnalisées du manifeste, telles que les chaînes avec des caractères spéciaux, doivent être placées entre guillemets. Par exemple:   >
   >
   >
   ```>
   >#EXT-CUSTOM-TAG:type=SpliceOut,ID=1,time=71819.7222,duration=30.0,url=
   >"www.example.com:8090?parameter1=xyz&parameter2=abc"
   >```  >
   >



* Si l’ du échoue en raison d’un format de balise personnalisé, la propriété content contient toujours les données brutes de la balise, c’est-à-dire la chaîne située après le deux-points. Aucune erreur n’est générée dans ce cas.

| Elément | Description |
|---|---|
| BALISE, ID3 | Types possibles pour les métadonnées minutées. |
| `@property (nonatomic, assign) CMTime time` | Position temporelle, par rapport au  du contenu principal, où ces métadonnées ont été insérées dans le flux. |
| `@property (nonatomic, assign) PTTimedMetadataType type` | Renvoie le type des métadonnées minutées. |
| `@property (nonatomic, retain) NSString *metadataId` | Renvoie l’ID extrait des attributs de balise/indice. Sinon, une valeur aléatoire unique est fournie. |
| `@property (nonatomic, retain) NSString *name` | Renvoie le nom du repère, qui est généralement le nom de la balise HLS. |

