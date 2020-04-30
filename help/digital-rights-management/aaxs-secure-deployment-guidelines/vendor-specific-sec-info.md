---
seo-title: Informations de sécurité spécifiques au fournisseur
title: Informations de sécurité spécifiques au fournisseur
uuid: 23186770-c73a-4802-bc30-fa9e4b47d9ba
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Informations de sécurité spécifiques au fournisseur{#vendor-specific-security-information}

Cette section contient des informations relatives à la sécurité des systèmes d’exploitation et des serveurs d’applications intégrés à votre solution Adobe Access.

Utilisez les liens fournis dans cette section pour rechercher des informations de sécurité spécifiques au fournisseur pour votre système d’exploitation et votre serveur d’applications.

## Informations de sécurité du système d’exploitation {#section-B6D9D6CEA7CC42A8A20346600EFB5E4E}

Lorsque vous sécurisez votre système d’exploitation, mettez en oeuvre avec soin les mesures décrites par le fournisseur de votre système d’exploitation, notamment :

* Définition et contrôle des utilisateurs, rôles et privilèges
* Journaux de surveillance et pistes d’audit
* Suppression des services et applications inutiles
* Sauvegarde de fichiers

Pour plus d&#39;informations sur la sécurité des systèmes d&#39;exploitation pris en charge par Adobe Access, reportez-vous aux ressources indiquées dans le tableau ci-dessous.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-ugl-kjz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Système d’exploitation </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Ressource de sécurité </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Microsoft® Windows Server® 2008 Enterprise ou Standard Edition </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Guide de sécurité de Windows Server 2008</i> </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Red Hat® Enterprise Linux® 5.4, 5.5 et 5.6. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Guide de sécurité de Red Hat Enterprise Linux 5</i> </p> </td> 
  </tr> 
 </tbody> 
</table>

Le tableau ci-dessous décrit certaines approches possibles pour réduire au minimum les vulnérabilités de sécurité détectées dans le système d’exploitation.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-whl-kjz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Elément </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Correctifs de sécurité </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Il existe un risque accru qu’un utilisateur non autorisé puisse accéder au serveur d’applications si les correctifs de sécurité et les mises à niveau du fournisseur ne sont pas appliqués en temps opportun. Testez les correctifs de sécurité avant de les appliquer aux serveurs de production. </p> <p class="- topic/p ">Créez également des stratégies et des procédures pour rechercher et installer régulièrement des correctifs. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Logiciel de protection antivirus </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Les analyseurs de virus peuvent identifier les fichiers infectés en recherchant une signature ou en recherchant un comportement inhabituel. Les analyseurs conservent leurs signatures de virus dans un fichier, qui est généralement stocké sur le disque dur local. Comme de nouveaux virus sont souvent découverts, vous devez fréquemment mettre à jour ce fichier pour que l'analyseur de virus puisse identifier tous les virus actuels. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">NTP (Network Time Protocol) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Pour assurer le bon fonctionnement et l’analyse de la médecine légale, veillez à ce que les serveurs Adobe Access et les packs Adobe Access restent à l’heure exacte. Utilisez une version sécurisée de NTP pour synchroniser l'heure sur tous les systèmes connectés à Internet. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Informations sur la sécurité du serveur d’applications {#section-EBB4EF371CFF4A848694CC240B23D404}

Lorsque vous sécurisez votre serveur d’applications, vous devez mettre en oeuvre les mesures décrites par le revendeur de votre serveur, notamment :

* Utilisation d’un nom d’utilisateur d’administrateur non évident
* Désactivation des services inutiles
* Sécurisation du gestionnaire de console
* Activation des cookies sécurisés
* Fermeture des ports inutiles
* Limitation des interfaces administratives par adresses ou domaines IP
* Utilisation de Java™ Security Manager

