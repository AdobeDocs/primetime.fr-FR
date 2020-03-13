---
seo-title: Utilisation de la ligne de commande
title: Utilisation de la ligne de commande
uuid: 273e9d3b-efeb-46fa-a4b1-f13247b4e498
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Utilisation de la ligne de commande {#command-line-usage}

Le Gestionnaire de  de révocation se trouve dans le répertoire \Reference Implementation\Command Line Tools sur le DVD. Pour exécuter l’outil, utilisez l’une des syntaxes suivantes :

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

* `destfile` indique où le de révocation sera écrit.
* `crlNumber` est un numéro de version non négatif du de révocation des certificats (CRL). Ce nombre doit être incrémenté chaque fois que la liste CRL est mise à jour.

Le tableau suivant décrit les options de ligne de commande présentées dans la syntaxe ci-dessus :

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
   <td colname="2" class="- topic/entry ">Indique l’emplacement du fichier de configuration. Si cette option n’est pas utilisée, le Gestionnaire de  de révocation recherche <span class="filepath"> flashaccesstools.properties</span> dans le répertoire de travail. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-d nom de fichier</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Affiche des informations sur le  de révocation. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e date</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Facultatif) Date d’expiration du de révocation. Utilisez le format <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj</span> ou <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj-h24:min:sec</span> (par exemple, 2009-01-31-14:30:00 représente le 31 janvier à 14h30). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f nom_fichier[fichier_certificat]</span> </td> 
   <td colname="2" class="- topic/entry ">Ajoute toutes les entrées du de révocation existant. Un seul fichier existant peut être spécifié. <p class="- topic/p ">Si cette  existante a été signée avec des informations d’identification différentes de celle utilisée pour signer le nouvel  de, spécifiez son fichier de certificat en suivant cette procédure afin que sa signature puisse être vérifiée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et que -o n'est pas défini, une erreur est renvoyée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Si le fichier de destination existe déjà, écrasez-le sans invite. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-r issuerName serialNumber revocationDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Révoque le certificat identifié par <span class="codeph"> le nom</span> de l’émetteur et le <span class="codeph"> numérode série</span> à la date donnée. L’ <span class="codeph"> émetteurName</span> doit suivre le format de nom 509 (par exemple, <span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>). Spécifiez des numéros de série sous forme hexadécimale. Indiquez la date de révocation comme <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj</span> ou <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj-h24:min:sec</span>, par exemple 2008-12-1 ou 2008-12-1-00:00:00 pour minuit le 1er décembre 2008. Si la date de révocation n’est pas spécifiée, la date actuelle est utilisée. </p> </td> 
  </tr> 
 </tbody> 
</table>

