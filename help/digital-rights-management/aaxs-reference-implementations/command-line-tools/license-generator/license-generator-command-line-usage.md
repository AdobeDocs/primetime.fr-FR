---
title: Utilisation de la ligne de commande
description: Utilisation de la ligne de commande
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

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

`metadata` est un fichier .metadata contenant les métadonnées DRM d’accès Adobe. Ce fichier peut être obtenu à partir de contenu protégé à l’aide de la variable `-d -m` de Media Packager.

Pour afficher une licence générée précédemment, utilisez la syntaxe suivante :

```
    java -jar AdobeLicenseGenerator.jar -d 
<i class="+ topic ph hi-d="" i "="">
  license
</i class="+ topic>
```

`license` est un fichier contenant une licence d’accès aux Adobes générée par le générateur de licences.

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
   <td colname="2" class="- topic/entry "> Indiquez l’emplacement du fichier de configuration. Si cette option n’est pas utilisée, le générateur de licences recherche flashaccesstools.properties dans le répertoire de travail. Les options spécifiées sur la ligne de commande sont prioritaires sur celles présentes dans le fichier de configuration. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <i class="+ topic/ph hi-d/i "><span class="+ topic/ph pr-d/codeph codeph"> prensefile</span></i> </p> </td> 
   <td colname="2" class="- topic/entry "> Affichez des informations sur une licence déjà générée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-leaf-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Générez une licence feuille et écrivez la sortie dans un fichier spécifié. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-m metadata-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Spécifiez les métadonnées de contenu pour lesquelles générer une licence. (Obligatoire pour générer une licence) </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et <span class="codeph"> -o</span> n’est pas définie, une erreur est renvoyée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Si le fichier de destination existe déjà, écrasez-le sans invite. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-policy-num</span> </td> 
   <td colname="2" class="- topic/entry "> Si les métadonnées contiennent plusieurs stratégies, indiquez le nombre de stratégies à utiliser (en commençant par 1) pour générer la licence. Si elle n’est pas spécifiée, la première stratégie est utilisée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-r recipient-cert</span> </td> 
   <td colname="2" class="- topic/entry ">Générez une licence pour le destinataire spécifié. Un certificat de périphérique ou de domaine peut être utilisé. Multiple <span class="+ topic/ph pr-d/codeph codeph"> -r </span>des options peuvent être spécifiées pour créer une licence pour plusieurs destinataires. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-root-root-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Générez une licence racine et écrivez la sortie dans le fichier spécifié. </td> 
  </tr> 
 </tbody> 
</table>
