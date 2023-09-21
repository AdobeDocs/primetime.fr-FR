---
title: Gestionnaire de liste de révocation DRM
description: Gestionnaire de liste de révocation DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# Gestionnaire de liste de révocation DRM {#policy-revocation-list-manager}

Utilisez l’outil de ligne de commande Primetime DRM Revocation List Manager ( [!DNL AdobeRevocationListManager.jar]) pour créer et gérer des listes de révocation et vérifier si des stratégies ont été révoquées.

Avant l’exécution [!DNL AdobeRevocationListManager.jar], vous devez définir les propriétés dans la variable *Gestionnaire de listes de mise à jour de stratégie et propriétés du gestionnaire de listes de révocation* de votre fichier de configuration.

>[!NOTE]
>
>Vous pouvez également spécifier toutes les propriétés du Gestionnaire de listes de révocation à partir de la ligne de commande.

## Utilisation de la ligne de commande du gestionnaire de listes de révocation {#revocation-list-manager-command-line-usage}

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

* `destfile` spécifie le nom du fichier dans lequel les propriétés de la liste de révocation sont enregistrées.
* `crlNumber` représente un numéro de version non négatif de la liste de révocation des certificats (CRL). Vous devez incrémenter ce nombre chaque fois que la liste CRL est mise à jour.

**Tableau 5 : Options de ligne de commande**

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
   <td colname="2" class="- topic/entry "><p class="- topic/p ">Indique le nom et l’emplacement du fichier de configuration. </p><p class="- topic/p ">Si vous ne spécifiez aucun nom ou emplacement, le Gestionnaire de listes de révocation DRM recherche <span class="filepath"> flashaccesstools.properties</span> dans le répertoire de travail actuel. </p><p>Remarque : les options que vous spécifiez sur la ligne de commande sont prioritaires sur celles que vous spécifiez dans le fichier de configuration. </p>Indique l’emplacement du fichier de configuration. Si vous n’appliquez pas cette option, le gestionnaire de listes de révocation recherche <span class="filepath"> flashaccesstools.properties</span> dans le répertoire de travail. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-d filename</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Affiche des informations sur la liste de révocation. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e date</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Facultatif) Date d’expiration de la liste de révocation. Utilisez l’un des formats suivants : 
     <ul id="ul_2C89F8183C3647C593CB67576D9DED07"> 
      <li id="li_A866F6CBCB464193A119A6609C8F3B2A"><span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj</span> </li> 
      <li id="li_B5F9F6C995E64464838DDE447848F707"><span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj-h24:min:sec</span> </li> 
     </ul>Par exemple, 2009-01-31-14:30:00 représente le 31 janvier à 14 h 30. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f filename[certfile]</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Ajoute toutes les entrées de la liste de révocation existante. Vous pouvez uniquement spécifier un fichier existant. </p> <p class="- topic/p ">Si la liste existante a été signée avec des informations d’identification autres que celle que vous avez utilisée pour signer la nouvelle liste, vous devez spécifier son fichier de certificat en regard de pour vérifier sa signature. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et <span class="codeph"> -o</span> n’est pas définie, une erreur se produit. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Si le fichier de destination existe déjà, vous pouvez le remplacer sans y être invité. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-r issuerName serialNumber revocationDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Révoque le certificat qui a été identifié par <span class="codeph"> issuerName</span> et <span class="codeph"> serialNumber</span> à la date spécifiée. La variable <span class="codeph"> issuerName</span> doit utiliser le format de nom 509. Par exemple : <span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>. </p> <p>Vous devez spécifier les numéros de série dans un format hexadécimal. Vous devez également spécifier la date de révocation dans l’un des formats suivants : 
     <ul id="ul_1524FBC6818248F3A2B271243E649400"> 
      <li id="li_BC618EA2332D42A59B1B5434CAFFD2AF"><span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj</span> </li> 
      <li id="li_97F77810D20C4CF2944EFCFF5DFAE467"><span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj-h24:min:sec</span> </li> 
     </ul>Par exemple, 2008-12-1 ou 2008-12-1-00:00:00 pour minuit le 1er décembre 2008. Si vous ne spécifiez pas la date de révocation, la date courante est automatiquement appliquée. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Propriétés de configuration {#configuration-properties}

Vous devez appliquer des informations d’identification pour signer des listes de révocation. Les propriétés suivantes du gestionnaire de listes de révocation spécifient un fichier PKCS12 qui comprend des informations d’identification pour la signature des listes de révocation (certificat du serveur de licence), ainsi que le mot de passe du certificat :

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`
