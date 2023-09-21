---
title: Informations de sécurité spécifiques au fournisseur
description: Informations de sécurité spécifiques au fournisseur
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Informations de sécurité spécifiques au fournisseur{#vendor-specific-security-information}

Cette section contient des informations sur la sécurité des systèmes d’exploitation et des serveurs d’applications intégrés à votre solution Adobe Access.

Suivez les liens fournis dans cette section pour trouver des informations de sécurité spécifiques à un fournisseur pour votre système d’exploitation et votre serveur d’applications.

## Informations sur la sécurité du système d’exploitation {#section-B6D9D6CEA7CC42A8A20346600EFB5E4E}

Lorsque vous sécurisez votre système d’exploitation, implémentez soigneusement les mesures décrites par le fournisseur de votre système d’exploitation, notamment :

* Définition et contrôle des utilisateurs, des rôles et des privilèges
* Surveillance des journaux et des journaux d’audit
* Suppression des services et applications inutiles
* Sauvegarde de fichiers

Pour plus d’informations sur la sécurité des systèmes d’exploitation pris en charge par Adobe Access, reportez-vous aux ressources indiquées dans le tableau ci-dessous.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-ugl-kjz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Système d’exploitation </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Ressource de sécurité </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Microsoft® Windows Server® 2008 Édition Enterprise ou Standard </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Guide de sécurité de Windows Server 2008</i> </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Red Hat® Enterprise Linux® 5.4, 5.5 et 5.6. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Guide de sécurité Red Hat Enterprise Linux 5</i> </p> </td> 
  </tr> 
 </tbody> 
</table>

Le tableau suivant décrit certaines approches possibles pour réduire les vulnérabilités de sécurité du système d’exploitation.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-whl-kjz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Élément </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Correctifs de sécurité </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Le risque augmente qu’un utilisateur non autorisé puisse accéder au serveur d’applications si les correctifs de sécurité et les mises à niveau du fournisseur ne sont pas appliqués en temps voulu. Testez les correctifs de sécurité avant de les appliquer aux serveurs de production. </p> <p class="- topic/p ">Créez également des stratégies et des procédures pour vérifier et installer régulièrement les correctifs. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Logiciels de protection anti-virus </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Les analyseurs de virus peuvent identifier les fichiers infectés en recherchant une signature ou en observant un comportement inhabituel. Les analyseurs conservent leurs signatures de virus dans un fichier, qui est généralement stocké sur le disque dur local. Comme de nouveaux virus sont souvent découverts, vous devez fréquemment mettre à jour ce fichier pour que le scanner de virus identifie tous les virus actuels. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">NTP (Network Time Protocol) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Pour assurer le bon fonctionnement et l’analyse médico-légale, veillez à disposer de temps précis sur les serveurs Adobe Access et les packages Adobe Access. Utilisez une version sécurisée de NTP pour synchroniser l’heure sur tous les systèmes connectés à Internet. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Informations sur la sécurité du serveur d’applications {#section-EBB4EF371CFF4A848694CC240B23D404}

Lorsque vous sécurisez votre serveur d’applications, vous devez mettre en oeuvre les mesures décrites par le fournisseur de votre serveur, notamment :

* Utilisation d’un nom d’utilisateur administrateur non évident
* Désactivation des services inutiles
* Sécurisation du gestionnaire de console
* Activation des cookies sécurisés
* Fermeture des ports inutiles
* Limitation des interfaces administratives par adresses ou domaines IP
* Utilisation de Java™ Security Manager
