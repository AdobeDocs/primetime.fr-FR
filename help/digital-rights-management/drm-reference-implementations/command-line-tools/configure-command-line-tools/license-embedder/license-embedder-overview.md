---
title: Présentation
description: Présentation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# Incorporer de licence DRM {#license-embedder}

Utilisation [!DNL AdobeLicenseEmbedder.jar] pour incorporer des licences prégénérées dans le contenu protégé par Media Packager.

## Utilisation de la ligne de commande de l’incorporation de licences {#license-embedder-command-line-usage}

```
java -jar AdobeLicenseEmbedder.jar sourcefile destfile [options]
```

* `sourcefile` représente un fichier chiffré.
* `destfile` spécifie le nom du fichier dans lequel le contenu chiffré avec la licence incorporée est enregistré.

  Si vous spécifiez un répertoire, le fichier est enregistré dans le répertoire de destination. Le nom du fichier source devient également le nom du fichier enregistré dans le répertoire de destination.

Le tableau suivant décrit les options de ligne de commande que vous pouvez spécifier :

**Tableau 7 : Options**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_hnl_2sy_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Option de ligne de commande </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l nom_fichier_de_licence </span> </td> 
   <td colname="2" class="- topic/entry "> Nom du fichier contenant la licence que vous souhaitez incorporer. Vous pouvez spécifier plusieurs <span class="codeph"> -l </span> options pour incorporer plusieurs licences. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -m metadata-filename </span> </td> 
   <td colname="2" class="- topic/entry "> Indique les métadonnées de contenu pour lesquelles vous pouvez générer une licence. Cette option est requise pour générer une licence. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et que la variable <span class="codeph"> -o </span> n’a pas été appliqué, une erreur se produit. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> Si le fichier de destination existe déjà, vous pouvez le remplacer sans y être invité. </td> 
  </tr> 
 </tbody> 
</table>
