---
description: Les systèmes d’exploitation et les serveurs d’applications sont inclus dans votre solution Adobe Primetime DRM.
title: Informations de sécurité spécifiques au fournisseur
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# Informations de sécurité spécifiques au fournisseur{#vendor-specific-security-information}

Les systèmes d’exploitation et les serveurs d’applications sont inclus dans votre solution Adobe Primetime DRM.

Pour obtenir des informations de sécurité spécifiques à un fournisseur pour votre système d’exploitation et votre serveur d’applications, voir Utilisation du serveur de clés Adobe Primetime DRM.

## Informations sur la sécurité du système d’exploitation {#section_53CAD802FCA54C4D8CE0C4E1B3045E52}

Lorsque vous sécurisez votre système d’exploitation, vous devez mettre en oeuvre les mesures décrites par le fournisseur de votre système d’exploitation.

Voici quelques mesures :

* Définition et contrôle des utilisateurs, des rôles et des privilèges
* Surveillance des journaux et des journaux d’audit
* Suppression des services et applications inutiles
* Sauvegarde de fichiers

Voici quelques informations sur les systèmes d’exploitation pris en charge par Adobe Primetime DRM :

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_ugl_kjz_n4"> 
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

Voici quelques informations sur les méthodes permettant de réduire au minimum les vulnérabilités de sécurité du système d’exploitation :

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_whl_kjz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Élément </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Correctifs de sécurité </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Le risque augmente qu’un utilisateur non autorisé puisse accéder au serveur d’applications si les correctifs de sécurité et les mises à niveau du fournisseur ne sont pas appliqués en temps voulu. </p> <p>Remarque : Assurez-vous de tester les correctifs de sécurité avant de les appliquer aux serveurs de production. </p> <p class="- topic/p ">Vous devez créer des stratégies et des procédures pour vérifier et installer régulièrement les correctifs. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Logiciels de protection anti-virus </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Les programmes antivirus peuvent identifier les fichiers infectés en recherchant une signature ou un comportement inhabituel. </p> <p>Les analyseurs conservent leurs signatures de virus dans un fichier, qui est généralement stocké sur le disque dur local. Les nouveaux virus sont souvent découverts, vous devez donc vous assurer que ce fichier est régulièrement mis à jour. De cette façon, les analyseurs de virus peuvent toujours identifier tous les virus actuels. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">NTP (Network Time Protocol) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Pour assurer le bon fonctionnement et l’analyse médico-légale, veillez à ce que les serveurs et les modules de gestion des données (DRM) Primetime restent à l’heure exacte. Utilisez une version sécurisée de NTP pour synchroniser l’heure DRM Primetime sur tous les systèmes connectés à Internet. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Informations sur la sécurité du serveur d’applications {#section_22986936F1A547CEAB2D97E9E9D4825C}

Lorsque vous sécurisez votre serveur d’applications, vous devez mettre en oeuvre les mesures décrites par le fournisseur de votre serveur.

Voici quelques-unes de ces mesures :

* Utilisation d’un nom d’utilisateur administrateur non évident
* Désactivation des services inutiles
* Sécurisation du gestionnaire de console
* Activation des cookies sécurisés
* Fermeture des ports inutiles
* Limitation des interfaces administratives par adresses ou domaines IP
* Utilisation de Java™ Security Manager
