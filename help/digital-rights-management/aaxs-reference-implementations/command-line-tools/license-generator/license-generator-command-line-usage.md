---
seo-title: Utilisation de la ligne de commande
title: Utilisation de la ligne de commande
uuid: b3a995de-653e-491a-9262-86dc56b9ce31
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Utilisation de la ligne de commande {#command-line-usage}

Pour générer une licence, utilisez la syntaxe suivante :

```
    java -jar AdobeLicenseGenerator.jar -m 
<i class="+ topic ph hi-d="" i "="">
 metadata 
 <i class="+ topic ph hi-d="" i "="">
   [options]
 </i class="+ topic>
</i class="+ topic>
```

`metadata` est un fichier .metadata contenant les métadonnées DRM d&#39;Adobe Access. Ce fichier peut être obtenu à partir d’un contenu protégé à l’aide de l’ `-d -m` option Media Packager.

Pour afficher une licence générée précédemment, utilisez la syntaxe suivante :

```
    java -jar AdobeLicenseGenerator.jar -d 
<i class="+ topic ph hi-d="" i "="">
  license
</i class="+ topic>
```

`license` est un fichier contenant une licence Adobe Access générée par le générateur de licences.

Le tableau suivant décrit les options de ligne de commande qui peuvent être spécifiées avec la syntaxe mentionnée précédemment :

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_skr_vry_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Option de ligne de commande </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-c configfile</span> </td> 
   <td colname="2" class="- topic/entry "> Spécifiez l’emplacement du fichier de configuration. Si cette option n’est pas utilisée, le générateur de licences recherche flashaccesstools.properties dans le répertoire de travail. Les options spécifiées sur la ligne de commande sont prioritaires sur celles du fichier de configuration. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <i class="+ topic/ph hi-d/i "><span class="+ topic/ph pr-d/codeph codeph"> fichier de licence</span></i> </p> </td> 
   <td colname="2" class="- topic/entry "> Affichez des informations sur une licence déjà générée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-leaf-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Générez une licence feuille et écrivez la sortie dans un fichier spécifié. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-m nom_fichier_métadonnées</span> </td> 
   <td colname="2" class="- topic/entry "> Spécifiez les métadonnées de contenu pour lesquelles générer une licence. (Obligatoire pour générer une licence) </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et que <span class="codeph"> -o</span> n'est pas défini, une erreur est renvoyée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Si le fichier de destination existe déjà, remplacez-le sans invite. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-policy-num</span> </td> 
   <td colname="2" class="- topic/entry "> Si les métadonnées contiennent plusieurs stratégies, indiquez le numéro de la stratégie à utiliser (à partir de 1) pour générer la licence. Si elle n’est pas spécifiée, la première stratégie est utilisée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-r destinataire-cert</span> </td> 
   <td colname="2" class="- topic/entry ">Générez une licence pour le destinataire spécifié. Un certificat de périphérique ou de domaine peut être utilisé. Plusieurs <span class="+ topic/ph pr-d/codeph codeph"> options </span>-r peuvent être spécifiées pour créer une licence pour plusieurs destinataires. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-root-root-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Générez une licence racine et écrivez la sortie dans le fichier spécifié. </td> 
  </tr> 
 </tbody> 
</table>

