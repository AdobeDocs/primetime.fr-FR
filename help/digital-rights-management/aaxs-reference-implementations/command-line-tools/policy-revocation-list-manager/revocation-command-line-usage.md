---
title: Utilisation de la ligne de commande
description: Utilisation de la ligne de commande
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Utilisation de la ligne de commande {#command-line-usage}

Revocation List Manager se trouve dans le répertoire \Reference Implementation\Command Line Tools sur le DVD. Pour exécuter l’outil, utilisez l’une des syntaxes suivantes :

```
    java -jar AdobeRevocationListManager.jar 
<i class="+ topic ph hi-d="" i "="">
 destfile 
 <i class="+ topic ph hi-d="" i "="">
  crlNumber [
  <i class="+ topic ph hi-d="" i "="">
   options] 
       java -jar AdobeRevocationListManager.jar -d 
   <i class="+ topic ph hi-d="" i "="">
     filename
   </i class="+ topic>
  </i class="+ topic>
 </i class="+ topic>
</i class="+ topic>
```

* `destfile` indique où la liste de révocation sera écrite.
* `crlNumber` est un numéro de version non négatif de la liste de révocation des certificats (CRL). Ce nombre doit être incrémenté chaque fois que la liste CRL est mise à jour.

Le tableau suivant contient des descriptions des options de ligne de commande affichées dans la syntaxe ci-dessus :

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_a3y_wqy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Option de ligne de commande </th> 
   <th colname="2" class="- topic/entry entry"> Description </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-c configfile</span> </td> 
   <td colname="2" class="- topic/entry ">Indique l’emplacement du fichier de configuration. Si cette option n’est pas utilisée, le gestionnaire de liste de révocation recherche <span class="filepath"> flashaccesstools.properties</span> dans le répertoire de travail. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-d filename</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Affiche des informations sur la liste de révocation. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e date</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Facultatif) Date d’expiration de la liste de révocation. Utiliser le format <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj</span> ou <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj-h24:min:sec</span> (par exemple, 2009-01-31-14:30:00 représente le 31 janvier à 14 h 30). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f filename[certfile]</span> </td> 
   <td colname="2" class="- topic/entry ">Ajoute toutes les entrées de la liste de révocation existante. Un seul fichier existant peut être spécifié. <p class="- topic/p ">Si cette liste existante a été signée avec des informations d’identification différentes de celle utilisée pour signer la nouvelle liste, spécifiez son fichier de certificat suivant, afin que sa signature puisse être vérifiée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et que -o n’est pas défini, une erreur est renvoyée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Si le fichier de destination existe déjà, écrasez-le sans invite. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-r issuerName serialNumber revocationDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Révoque le certificat identifié par <span class="codeph"> issuerName</span> et <span class="codeph"> serialNumber</span> à la date donnée. La variable <span class="codeph"> issuerName</span> doit respecter le format de nom 509 (par exemple, <span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>). Spécifiez les numéros de série sous forme hexadécimale. Indiquez la date de révocation comme <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj</span> ou <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj-h24:min:sec</span>, par exemple 2008-12-1 ou 2008-12-1-00:00:00 pour minuit le 1er décembre 2008. Si la date de révocation n’est pas spécifiée, la date courante est utilisée. </p> </td> 
  </tr> 
 </tbody> 
</table>
