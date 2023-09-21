---
title: Utilisation de la ligne de commande
description: Utilisation de la ligne de commande
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Utilisation de la ligne de commande {#command-line-usage}

Pour incorporer une licence, utilisez la syntaxe suivante :

```
    java -jar AdobeLicenseEmbedder.jar  
<i class="+ topic ph hi-d="" i "="">
  sourcefile destfile [options] 
</i class="+ topic>
```

* `sourcefile` est un fichier FLV ou F4V chiffré.
* `destfile` indique l’emplacement d’écriture du contenu chiffré avec la licence incorporée. Si un répertoire est spécifié, le fichier est enregistré dans ce répertoire avec le même nom de fichier que le fichier source, mais le répertoire ne doit pas être celui qui contient le fichier source.

Le tableau suivant décrit les options de ligne de commande qui peuvent être spécifiées avec la syntaxe mentionnée précédemment :

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
   <td colname="2" class="- topic/entry "> Nom du fichier contenant la licence à incorporer. Multiple <span class="codeph"> -l </span> Les options peuvent être spécifiées pour incorporer plusieurs licences. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -m metadata-filename </span> </td> 
   <td colname="2" class="- topic/entry "> Spécifiez les métadonnées de contenu pour lesquelles générer une licence. (Obligatoire pour générer une licence) </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et <span class="codeph"> -o </span> n’est pas définie, une erreur est renvoyée. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> Si le fichier de destination existe déjà, écrasez-le sans invite. </td> 
  </tr> 
 </tbody> 
</table>
