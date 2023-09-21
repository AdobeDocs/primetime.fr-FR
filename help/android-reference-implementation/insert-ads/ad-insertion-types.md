---
description: TVSDK fournit actuellement une prise en charge intégrée des métadonnées du fournisseur de publicités pour les publicités TVSDK, les coupures publicitaires directes et les marqueurs publicitaires personnalisés.
title: Types d’insertion de publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Types d’insertion de publicités {#ad-insertion-types}

TVSDK fournit actuellement une prise en charge intégrée des métadonnées du fournisseur de publicités pour les publicités TVSDK, les coupures publicitaires directes et les marqueurs publicitaires personnalisés.

Il prend en charge les types de processus d’insertion de publicités suivants pour le contenu VOD et le contenu direct/linéaire.

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
   <td colname="col1"> Publicités de prise de décision dans Adobe Primetime </td> 
   <td colname="col2">VOD <p>En direct </p> <p>Linéaire </p> </td> 
   <td colname="col3">L’implémentation de référence fournit <span class="codeph"> AuditudeMetadata</span> les informations de connexion au serveur pour Primetime et la prise de décision (précédemment connu sous le nom d’Auditude), en fonction des informations fournies dans la partie publicités Primetime.</a> du fichier de configuration JSON</a>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Pertes publicitaires directes </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">Vous devez fournir des URL de publicité dans le fichier JSON d’entrée. Lorsque TVSDK tente de résoudre une publicité, il appelle le résolveur de coupure publicitaire directe et résout les publicités en fonction des informations de coupures publicitaires directes fournies dans le fichier de configuration JSON.</a>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Marqueurs publicitaires personnalisés </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">Les marqueurs d’annonce personnalisés sont utiles lorsque le flux vidéo contient à la fois du contenu principal et des publicités, mais n’inclut pas d’informations relatives aux positions et à la durée de la publicité. Si les informations de positionnement de la publicité sont obtenues d’une autre manière, par exemple par le biais d’un système de gestion des actifs numériques externe, vous pouvez définir des marqueurs de publicité personnalisés et les transmettre à la chronologie du lecteur. <p>Pour configurer un lecteur pour l’insertion de publicités, vous devez transmettre des métadonnées publicitaires dans la section des métadonnées publicitaires personnalisées du fichier de configuration JSON.</a>, qui prend en charge l’implémentation du fournisseur d’annonces dans l’implémentation de référence. </p> </td>
  </tr>
 </tbody>
</table>
