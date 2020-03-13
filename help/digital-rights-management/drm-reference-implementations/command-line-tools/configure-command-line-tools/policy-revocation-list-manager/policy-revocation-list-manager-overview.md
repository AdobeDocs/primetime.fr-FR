---
seo-title: Gestionnaire de de révocation DRM
title: Gestionnaire de de révocation DRM
uuid: 30ab5f54-4aac-4535-b30c-b4e5dbfbc475
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Gestionnaire de de révocation DRM {#policy-revocation-list-manager}

Utilisez l’outil de ligne de commande Gestionnaire de  de révocation DRM de Primetime [!DNL AdobeRevocationListManager.jar]pour créer et gérer les  de révocation et pour vérifier si les stratégies ont été révoquées.

Avant de vous exécuter [!DNL AdobeRevocationListManager.jar], vous devez définir les propriétés dans la section Gestionnaire de  de mise à jour de la *stratégie et Propriétés* du Gestionnaire de de révocation de votre fichier de configuration.

>[!NOTE]
>
>Vous pouvez également spécifier toutes les propriétés du Gestionnaire de  de révocation à partir de la ligne de commande.

## Utilisation de la ligne de commande du Gestionnaire  de révocation {#revocation-list-manager-command-line-usage}

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

* `destfile` indique le nom du fichier dans lequel les propriétés du de révocation sont enregistrées.
* `crlNumber` représente un numéro de version non négatif du de révocation des certificats (CRL). Vous devez incrémenter ce nombre chaque fois que la liste CRL est mise à jour.

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
   <td colname="2" class="- topic/entry "><p class="- topic/p ">Indique le nom et l’emplacement du fichier de configuration. </p><p class="- topic/p ">Si vous ne spécifiez pas de nom ou d’emplacement, le Gestionnaire de de révocation DRM recherche <span class="filepath"> flashaccesstools.properties</span> dans le répertoire de travail actuel. </p><p>Remarque :  Les options que vous spécifiez sur la ligne de commande sont prioritaires sur les options que vous spécifiez dans le fichier de configuration. </p>Indique l’emplacement du fichier de configuration. Si vous n’appliquez pas cette option, le Gestionnaire de  de révocation recherche <span class="filepath"> flashaccesstools.properties</span> dans le répertoire de travail. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-d nom de fichier</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Affiche des informations sur le  de révocation. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e date</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">(Facultatif) Date d’expiration du de révocation. Utilisez l’un des formats suivants : 
     <ul id="ul_2C89F8183C3647C593CB67576D9DED07"> 
      <li id="li_A866F6CBCB464193A119A6609C8F3B2A"><span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj</span> </li> 
      <li id="li_B5F9F6C995E64464838DDE447848F707"><span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj-h24:min:sec</span> </li> 
     </ul>Par exemple, 2009-01-31-14:30:00 représente le 31 janvier à 14:30. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f nom_fichier[fichier_certificat]</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Ajoute toutes les entrées du de révocation existant. Vous ne pouvez spécifier qu’un seul fichier existant. </p> <p class="- topic/p ">Si le existant a été signé avec des informations d’identification autres que celle que vous avez utilisée pour signer le nouvel , vous devez spécifier son fichier de certificat en regard de la signature. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et que <span class="codeph"> -o</span> n’est pas défini, une erreur se produit. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Si le fichier de destination existe déjà, vous pouvez le remplacer sans être invité à le faire. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-r issuerName serialNumber revocationDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Révoque le certificat qui a été identifié par <span class="codeph"> le nom</span> de l’émetteur et le <span class="codeph"> numérode série</span> à la date spécifiée. L’ <span class="codeph"> émetteurName</span> doit utiliser le format de nom 509. Par exemple, <span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>. </p> <p>Vous devez spécifier les numéros de série au format hexadécimal. Vous devez également spécifier la date de révocation dans l’un des formats suivants : 
     <ul id="ul_1524FBC6818248F3A2B271243E649400"> 
      <li id="li_BC618EA2332D42A59B1B5434CAFFD2AF"><span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj</span> </li> 
      <li id="li_97F77810D20C4CF2944EFCFF5DFAE467"><span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj-h24:min:sec</span> </li> 
     </ul>Par exemple, 2008-12-1 ou 2008-12-1-00:00:00 pour minuit le 1er décembre 2008. Si vous ne spécifiez pas la date de révocation, la date actuelle est automatiquement appliquée. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Propriétés de configuration {#configuration-properties}

Vous devez appliquer des informations d’identification pour signer le  de révocation. Les propriétés suivantes du Gestionnaire de  de révocation spécifient un fichier PKCS12 qui contient les informations d’identification pour la signature du de révocation (certificat du serveur de licences), ainsi que le mot de passe du certificat :

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`