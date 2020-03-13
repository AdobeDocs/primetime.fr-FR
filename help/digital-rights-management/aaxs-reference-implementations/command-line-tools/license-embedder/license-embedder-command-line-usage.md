---
seo-title: Utilisation de la ligne de commande
title: Utilisation de la ligne de commande
uuid: 72117619-a723-49d3-9aa9-5eefcf5b0916
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

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
* `destfile` indique où le contenu chiffré avec la licence incorporée sera écrit. Si un répertoire est spécifié, le fichier est enregistré dans ce répertoire en utilisant le même nom de fichier que le fichier source, mais le répertoire ne doit pas être celui qui contient le fichier source.

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
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l nom_fichier_licence </span> </td> 
   <td colname="2" class="- topic/entry "> Nom du fichier contenant la licence à incorporer. Plusieurs options <span class="codeph"> -l </span> peuvent être spécifiées pour incorporer plusieurs licences. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -m metadata-filename </span> </td> 
   <td colname="2" class="- topic/entry "> Spécifiez les métadonnées de contenu pour lesquelles générer une licence. (Obligatoire pour générer une licence) </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et que <span class="codeph"> -o </span> n'est pas défini, une erreur est renvoyée. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> Si le fichier de destination existe déjà, écrasez-le sans invite. </td> 
  </tr> 
 </tbody> 
</table>

