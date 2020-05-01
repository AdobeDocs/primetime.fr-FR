---
seo-title: Utilisation de la ligne de commande
title: Utilisation de la ligne de commande
uuid: 1c3a450d-5d9c-4437-89dd-1bd8719268b7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Utilisation de la ligne de commande {#command-line-usage}

Policy Update Liste Manager se trouve dans le répertoire \Reference Implementation\Command Line Tools sur le DVD. Pour créer une liste de mise à jour de stratégie, utilisez la syntaxe suivante :

```
    java -jar AdobePolicyUpdateListManager.jar  
<i class="+ topic ph hi-d="" i "="">
  destfile [ 
 <i class="+ topic ph hi-d="" i "="">
   options]  
 </i class="+ topic> 
</i class="+ topic>
```

* `destfile` indique où la liste de mise à jour de la stratégie sera écrite.

Pour vue d’une liste de mise à jour de stratégie existante, utilisez la syntaxe suivante :

```
    java -jar AdobePolicyUpdateListManager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  filename 
</i class="+ topic>
```

Le tableau suivant contient la description des options de ligne de commande affichées dans la syntaxe ci-dessus :

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique l’emplacement du fichier de configuration. Si cette option n'est pas utilisée, le Gestionnaire de Listes de mise à jour des stratégies recherche <span class="filepath"> flashaccesstools.properties </span> dans le répertoire de travail. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -d nom de fichier </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Affiche des informations sur la liste de mise à jour de la stratégie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e date </span> </td> 
   <td colname="2" class="- topic/entry "> (Facultatif) Date d’expiration de la liste de mise à jour de la stratégie. Utilisez le format <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj </span> ou <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj-h24:min:sec </span> (par exemple, 2009-01-31-14:30:00 représente le 31 janvier à 14:30 PM). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -f nom_fichier [certfile] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ajoute toutes les entrées de la liste de mise à jour de stratégie existante. Un seul fichier existant peut être spécifié. </p> <p class="- topic/p ">Si cette liste existante a été signée avec des informations d’identification différentes de celle utilisée pour signer la nouvelle liste, spécifiez son fichier de certificat afin que sa signature puisse être vérifiée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et que <span class="codeph"> -o </span> n'est pas défini, une erreur est renvoyée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si le fichier de destination existe déjà, remplacez-le sans invite. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r identifiant de stratégie </span><span class="+ topic/ph pr-d/codeph codeph"> date </span> " <span class="+ topic/ph pr-d/codeph codeph"> code motif </span>" " <span class="+ topic/ph pr-d/codeph codeph"> texte motif </span>" "  raisonURL "<span class="+ topic/ph pr-d/codeph codeph"></span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Facultatif) Révoque l’ID de stratégie à la date spécifiée. Un code de motif, un texte de motif et une URL de motif facultatifs peuvent également être fournis. Spécifiez une chaîne vide "" pour indiquer qu’aucune valeur n’est fournie pour les paramètres facultatifs. Indiquez la date comme <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj </span> ou <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj-h24:min:s </span> (par exemple, 2008-12-1 ou 2008-12-1-00:00:00 pour minuit le 1er décembre 2008). Si aucune date n’est spécifiée, la date actuelle est utilisée. Le code motif doit être supérieur ou égal à 0. Plusieurs options -r peuvent être spécifiées. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-rf stratégieNom <span class="+ topic/ph pr-d/codeph codeph"> de fichier </span> Date <span class="+ topic/ph pr-d/codeph codeph"> " </span> Code de raison <span class="+ topic/ph pr-d/codeph codeph"> " " </span><span class="+ topic/ph pr-d/codeph codeph"> de motif" " URL de raison "</span><span class="+ topic/ph pr-d/codeph codeph"></span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Exécute la même action que l’indicateur -r, mais extrait l’identifiant de stratégie du fichier donné. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -u policyFilename " reasonCode" " reasonText" " reasonURL" </span> </td> 
   <td colname="2" class="- topic/entry "> <p>Remplace toute stratégie correspondante dans une demande de licence par cette stratégie à l’aide du code de raison indiqué (facultatif), du texte de motif (facultatif) et de l’URL de motif (facultatif). </p> <p>Spécifiez une chaîne vide "" pour indiquer qu’aucune valeur n’est fournie pour les paramètres facultatifs. </p> <p>Le code de motif doit être supérieur ou égal à <span class="codeph"> 0 </span>. Plusieurs options <span class="codeph"> -u </span> peuvent être spécifiées. </p> </td> 
  </tr> 
 </tbody> 
</table>

