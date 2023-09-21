---
title: Présentation
description: Présentation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# Gestionnaire de liste de mise à jour de stratégie DRM {#policy-update-list-manager}

Utilisez l’outil de ligne de commande Primetime DRM Policy Update List Manager ( [!DNL AdobePolicyUpdateListManager.jar]) pour créer et gérer des listes de mise à jour de stratégies DRM, et vérifier si des stratégies ont été mises à jour ou révoquées.

Avant d’exécuter l’outil de ligne de commande Gestionnaire de listes de mise à jour des stratégies, vous devez définir les propriétés dans la variable *Gestionnaire de listes de mise à jour de stratégie et propriétés du gestionnaire de listes de révocation* de votre fichier de configuration.

>[!NOTE]
>
>Vous pouvez également spécifier toutes les propriétés du gestionnaire de liste de mise à jour des stratégies à partir de la ligne de commande.

## Utilisation de la ligne de commande du gestionnaire de listes de mise à jour de stratégie {#policy-update-list-manager-command-line-usage}

**Créez une liste de mise à jour de stratégie :**

```
java -jar AdobePolicyUpdateListManager.jar  
<i class="+ topic ph hi-d="" i "="">
  destfile [ 
 <i class="+ topic ph hi-d="" i "="">
   options]  
 </i class="+ topic> 
</i class="+ topic>
```

* `destfile` indique le nom du fichier dans lequel est écrite la liste de mise à jour de la stratégie DRM.

**Afficher une liste de mises à jour de stratégie existante :**

```
java -jar AdobePolicyUpdateListManager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  filename 
</i class="+ topic>
```

* `filename` Nom du fichier de liste de mise à jour de stratégie.

**Tableau 4 : Options de ligne de commande**

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique le nom et l’emplacement du fichier de configuration. </p> <p class="- topic/p ">Si vous ne spécifiez aucun nom ou emplacement, le Gestionnaire de listes de mise à jour de stratégie DRM recherche <span class="filepath"> flashaccesstools.properties </span> dans le répertoire de travail actuel. </p> <p>Remarque : les options que vous spécifiez sur la ligne de commande sont prioritaires sur celles que vous spécifiez dans le fichier de configuration. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -d filename </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Affiche des informations sur la liste de mise à jour de la stratégie DRM. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e date </span> </td> 
   <td colname="2" class="- topic/entry "> <p>(Facultatif) Date d’expiration de la liste de mise à jour de la stratégie DRM. </p> <p>Utiliser le format <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj </span> ou <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj-h24:min:sec </span> (par exemple, 2009-01-31-14:30:00 représente le 31 janvier à 14 h 30). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -f filename [certfile] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ajoute toutes les entrées de la liste de mise à jour de stratégie DRM existante. Vous pouvez uniquement spécifier un fichier existant. </p> <p class="- topic/p ">Si la liste existante a été signée avec des informations d’identification autres que celle utilisée pour signer la nouvelle liste, vous devez spécifier son fichier de certificat pour vérifier sa signature. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et <span class="codeph"> -o </span> n’est pas définie, une erreur se produit. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si le fichier de destination existe déjà, écrasez-le sans invite. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r policyID </span> <span class="+ topic/ph pr-d/codeph codeph"> date </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Facultatif) Permet d’appeler l’ID de stratégie DRM à la date spécifiée. Vous pouvez fournir un code de raison, un texte de raison et une URL de raison facultatifs. Vous devez spécifier une chaîne vide "" pour indiquer qu’aucune valeur n’est fournie pour les paramètres facultatifs. Vous pouvez spécifier la date dans la section <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj </span> ou <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj-h24:min:sec </span> dans ces formats. Par exemple, 2008-12-1 ou 2008-12-1-00:00:00 représente minuit le 1er décembre 2008). Si vous ne spécifiez pas de date, la date courante est automatiquement appliquée. Par conséquent, le code de raison doit être supérieur ou égal à 0. Vous pouvez également spécifier plusieurs options -r. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-rf <span class="+ topic/ph pr-d/codeph codeph"> policyFilename </span> <span class="+ topic/ph pr-d/codeph codeph"> date </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Exécute la même action que la variable <span class="codeph"> -r </span> . Cependant, il extrait l’identifiant de stratégie DRM d’un fichier spécifié. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -u policyFilename "reasonCode" "reasonText" "reasonURL" </span> </td> 
   <td colname="2" class="- topic/entry "> <p>Remplace toute stratégie DRM correspondante dans une demande de licence par cette stratégie DRM en utilisant le code de raison donné (facultatif), le texte de raison (facultatif) et l’URL de raison (facultatif). </p> <p>Une chaîne vide "" indique que vous n’avez fourni aucune valeur pour les paramètres facultatifs. </p> <p>Le code de raison doit être supérieur ou égal à <span class="codeph"> 0 </span>. Vous pouvez spécifier plusieurs <span class="codeph"> -u </span> options. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Propriétés de configuration {#configuration-properties}

Les propriétés suivantes du gestionnaire de liste de mise à jour de stratégie DRM Primetime définissent un fichier PKCS12 qui comprend des informations d’identification pour la signature de listes de révocation (certificat du serveur de licence), ainsi qu’un mot de passe.

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`
