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

Policy Update List Manager se trouve dans le répertoire \Reference Implementation\Command Line Tools sur le DVD. Pour créer une liste de mise à jour de stratégie, utilisez la syntaxe suivante :

```
    java -jar AdobePolicyUpdateListManager.jar  
<i class="+ topic ph hi-d="" i "="">
  destfile [ 
 <i class="+ topic ph hi-d="" i "="">
   options]  
 </i class="+ topic> 
</i class="+ topic>
```

* `destfile` indique l’emplacement d’écriture de la liste de mise à jour des stratégies.

Pour afficher une liste de mise à jour de stratégie existante, utilisez la syntaxe suivante :

```
    java -jar AdobePolicyUpdateListManager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  filename 
</i class="+ topic>
```

Le tableau suivant contient des descriptions des options de ligne de commande affichées dans la syntaxe ci-dessus :

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_ghb_jqy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Option de ligne de commande </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique l’emplacement du fichier de configuration. Si cette option n’est pas utilisée, le gestionnaire de liste de mise à jour des stratégies recherche <span class="filepath"> flashaccesstools.properties </span> dans le répertoire de travail. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -d filename </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Affiche des informations sur la liste des mises à jour de stratégie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e date </span> </td> 
   <td colname="2" class="- topic/entry "> (Facultatif) Date d’expiration de la liste de mise à jour de stratégie. Utiliser le format <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj </span> ou <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj-h24:min:sec </span> (par exemple, 2009-01-31-14:30:00 représente le 31 janvier à 14 h 30). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -f filename [certfile] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ajoute toutes les entrées de la liste de mise à jour de stratégie existante. Un seul fichier existant peut être spécifié. </p> <p class="- topic/p ">Si cette liste existante a été signée avec des informations d’identification différentes de celle utilisée pour signer la nouvelle liste, spécifiez son fichier de certificat afin que sa signature puisse être vérifiée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et <span class="codeph"> -o </span> n’est pas définie, une erreur est renvoyée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si le fichier de destination existe déjà, écrasez-le sans invite. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r policyID </span> <span class="+ topic/ph pr-d/codeph codeph"> date </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Facultatif) Permet d’appeler l’ID de stratégie à la date spécifiée. Vous pouvez également fournir un code de raison, un texte de raison et une URL de raison facultatifs. Spécifiez une chaîne vide "" pour indiquer qu’aucune valeur n’est fournie pour les paramètres facultatifs. Indiquez la date comme <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj </span> ou <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj-h24:min:sec </span> (par exemple, 2008-12-1 ou 2008-12-1-00:00:00 pour minuit le 1er décembre 2008). Si aucune date n’est spécifiée, la date actuelle est utilisée. Le code de raison doit être supérieur ou égal à 0. Plusieurs options -r peuvent être spécifiées. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-rf <span class="+ topic/ph pr-d/codeph codeph"> policyFilename </span> <span class="+ topic/ph pr-d/codeph codeph"> date </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Exécute la même action que l’indicateur -r, mais extrait l’identifiant de stratégie du fichier donné. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -u policyFilename "reasonCode" "reasonText" "reasonURL" </span> </td> 
   <td colname="2" class="- topic/entry "> <p>Remplace toute stratégie correspondante dans une demande de licence par cette stratégie à l’aide du code de raison donné (facultatif), du texte de raison (facultatif) et de l’URL de raison (facultatif). </p> <p>Spécifiez une chaîne vide "" pour indiquer qu’aucune valeur n’est fournie pour les paramètres facultatifs. </p> <p>Le code de raison doit être supérieur ou égal à <span class="codeph"> 0 </span>. Multiple <span class="codeph"> -u </span> Les options peuvent être spécifiées. </p> </td> 
  </tr> 
 </tbody> 
</table>
