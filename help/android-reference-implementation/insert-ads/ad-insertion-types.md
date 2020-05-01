---
description: Le SDK TVSDK fournit actuellement une prise en charge intégrée des métadonnées du fournisseur d’annonces pour les publicités TVSDK, les coupures publicitaires directes et les marqueurs d’annonces personnalisées.
seo-description: Le SDK TVSDK fournit actuellement une prise en charge intégrée des métadonnées du fournisseur d’annonces pour les publicités TVSDK, les coupures publicitaires directes et les marqueurs d’annonces personnalisées.
seo-title: Types d’insertion publicitaire
title: Types d’insertion publicitaire
uuid: 6b5c3555-1ddd-4215-8bb2-03d16bb818c5
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Types d’insertion publicitaire {#ad-insertion-types}

Le SDK TVSDK fournit actuellement une prise en charge intégrée des métadonnées du fournisseur d’annonces pour les publicités TVSDK, les coupures publicitaires directes et les marqueurs d’annonces personnalisées.

Il prend en charge les types suivants de workflows d’insertion de publicités pour VOD et de contenu direct/linéaire.

<table id="table_1C3A659BDDB7453CA953A103045FCA01"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Type d'insertion </th> 
   <th colname="col2" class="entry"> Pris en charge dans... </th> 
   <th colname="col3" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Publicités de prise de décision publicitaire Adobe Primetime </td> 
   <td colname="col2">VOD <p>Live </p> <p>Linéaire </p> </td> 
   <td colname="col3">L’implémentation de référence fournit des informations <span class="codeph"> AuditudeMetadata</span> pour la connexion au serveur pour Primetime et la prise de décision (anciennement Auditude), en fonction des informations fournies dans la partie</a> Publicités Primetime du fichier</a>de configuration JSON. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Interruptions publicitaires directes </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">Vous devez fournir des URL de publicité dans le fichier JSON d’entrée. Lorsque TVSDK tente de résoudre une publicité, il appelle le résolveur de coupures publicitaires directes et résout les publicités en fonction des informations de coupures publicitaires directes fournies dans le fichier</a>de configuration JSON. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Marqueurs publicitaires personnalisés </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">Les marqueurs publicitaires personnalisés sont utiles lorsque le flux vidéo contient à la fois le contenu principal et les publicités, mais n’inclut pas d’informations relatives aux emplacements et au timing de la publicité. Si les informations de positionnement de la publicité sont obtenues d’une autre manière, par exemple par le biais d’un CMS externe, vous pouvez définir des marqueurs publicitaires personnalisés et les transmettre à la chronologie du lecteur. <p>Pour configurer un lecteur pour l’insertion d’annonces, vous devez transmettre les métadonnées publicitaires dans la section des métadonnées publicitaires personnalisées du fichier</a>de configuration JSON, qui prend en charge l’implémentation des fournisseurs d’annonces dans l’implémentation des références. </p> </td>
  </tr>
 </tbody>
</table>