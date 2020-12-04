---
seo-title: Présentation
title: Présentation
uuid: 19d05867-c210-4cd0-bc2f-5dd75f5774e5
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Gestionnaire de mise à jour de la stratégie DRM {#policy-update-list-manager}

Utilisez l&#39;outil de ligne de commande Primetime DRM Policy Update Liste Manager ( [!DNL AdobePolicyUpdateListManager.jar]) pour créer et gérer des listes de mise à jour de stratégie DRM et vérifier si des stratégies ont été mises à jour ou révoquées.

Avant d&#39;exécuter l&#39;outil de ligne de commande Policy Update Liste Manager, vous devez définir les propriétés dans la section *Policy Update Liste Manager et Revocation Liste Manager Properties* de votre fichier de configuration.

>[!NOTE]
>
>Vous pouvez également spécifier toutes les propriétés du Gestionnaire de Listes de mise à jour des stratégies à partir de la ligne de commande.

## Mise à jour des stratégies Utilisation de la ligne de commande du Gestionnaire de Listes {#policy-update-list-manager-command-line-usage}

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

* `destfile` indique le nom du fichier dans lequel la liste de mise à jour de la stratégie DRM est écrite.

**Vue d’une liste de mise à jour de stratégie existante :**

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
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique le nom et l’emplacement du fichier de configuration. </p> <p class="- topic/p ">Si vous ne spécifiez ni nom ni emplacement, le Gestionnaire de Listes de mise à jour de stratégie DRM recherche <span class="filepath"> flashaccesstools.properties </span> dans le répertoire de travail actuel. </p> <p>Remarque :  Les options que vous spécifiez sur la ligne de commande sont prioritaires sur les options que vous spécifiez dans le fichier de configuration. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -d nom de fichier  </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Affiche des informations sur la liste de mise à jour de la stratégie DRM. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e date  </span> </td> 
   <td colname="2" class="- topic/entry "> <p>(Facultatif) Date d’expiration de la liste de mise à jour de la stratégie DRM. </p> <p>Utilisez le format <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj </span> ou <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj-h24:min:sec </span> (par exemple, 2009-01-31-14:30:00 représente le 31 janvier à 14:30 PM). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -f nom_fichier [certfile]  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ajoute toutes les entrées de la liste de mise à jour de stratégie DRM existante. Vous ne pouvez spécifier qu’un seul fichier existant. </p> <p class="- topic/p ">Si la liste existante a été signée avec des informations d’identification autres que celle utilisée pour signer la nouvelle liste, vous devez spécifier son fichier de certificat pour vérifier sa signature. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -noprompt  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et que <span class="codeph"> -o </span> n'est pas défini, une erreur se produit. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si le fichier de destination existe déjà, remplacez-le sans invite. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r policyID  </span> <span class="+ topic/ph pr-d/codeph codeph"> date  </span> "  <span class="+ topic/ph pr-d/codeph codeph"> code de raison  </span>" "  <span class="+ topic/ph pr-d/codeph codeph"> reasonText  </span>" "  <span class="+ topic/ph pr-d/codeph codeph"> reasonURL "</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Facultatif) Révoque l’ID de stratégie DRM à la date spécifiée. Vous pouvez fournir un code de motif, un texte de motif et une URL de motif facultatifs. Vous devez spécifier une chaîne vide "" pour indiquer qu'aucune valeur n'est fournie pour les paramètres facultatifs. Vous pouvez spécifier la date dans <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj </span> ou <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj-h24:min:sec </span> dans ces formats. Par exemple, 2008-12-1 ou 2008-12-1-00:00:00 représente minuit le 1er décembre 2008). Si vous ne spécifiez pas de date, la date actuelle est automatiquement appliquée. Par conséquent, le code de motif doit être supérieur ou égal à 0. Vous pouvez également spécifier plusieurs options -r. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-rf <span class="+ topic/ph pr-d/codeph codeph"> policyFilename </span> <span class="+ topic/ph pr-d/codeph codeph"> date </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Exécute la même action que l'option <span class="codeph"> -r </span>. Cependant, il extrait l'identifiant de stratégie DRM d'un fichier spécifié. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -u policyFilename " reasonCode" " reasonText" " reasonURL"  </span> </td> 
   <td colname="2" class="- topic/entry "> <p>Remplace toute stratégie DRM correspondante dans une demande de licence par cette stratégie DRM en utilisant le code de raison donné (facultatif), le texte de raison (facultatif) et l'URL de raison (facultatif). </p> <p>Une chaîne vide "" indique que vous n'avez fourni aucune valeur pour les paramètres facultatifs. </p> <p>Le code de motif doit être supérieur ou égal à <span class="codeph"> 0 </span>. Vous pouvez spécifier plusieurs options <span class="codeph"> -u </span>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Propriétés de configuration {#configuration-properties}

Les propriétés suivantes de Primetime DRM Policy Update Liste Manager spécifient un fichier PKCS12 qui contient des informations d’identification pour la signature de listes de révocation (certificat du serveur de licences), ainsi qu’un mot de passe.

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`