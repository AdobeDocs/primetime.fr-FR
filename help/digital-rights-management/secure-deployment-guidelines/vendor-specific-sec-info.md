---
description: Les systèmes d’exploitation et les serveurs d’applications sont inclus dans votre solution DRM Adobe Primetime.
seo-description: Les systèmes d’exploitation et les serveurs d’applications sont inclus dans votre solution DRM Adobe Primetime.
seo-title: Informations de sécurité spécifiques au fournisseur
title: Informations de sécurité spécifiques au fournisseur
uuid: 331baa42-5e19-40a5-bc74-0b1a2cb9370e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Informations de sécurité spécifiques au fournisseur{#vendor-specific-security-information}

Les systèmes d’exploitation et les serveurs d’applications sont inclus dans votre solution DRM Adobe Primetime.

Pour obtenir des informations de sécurité spécifiques au fournisseur pour votre système d’exploitation et votre serveur d’applications, voir Utilisation du serveur de clés DRM d’Adobe Primetime.

## Informations de sécurité du système d’exploitation {#section_53CAD802FCA54C4D8CE0C4E1B3045E52}

Lorsque vous sécurisez votre système d’exploitation, vous devez mettre en oeuvre les mesures décrites par le fournisseur de votre système d’exploitation.

Voici quelques-unes des mesures :

* Définition et contrôle des utilisateurs, rôles et privilèges
* Journaux de surveillance et pistes d’audit
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
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Microsoft® Windows Server® 2008 Enterprise ou Standard Edition </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Guide de sécurité de Windows Server 2008</i> </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Red Hat® Enterprise Linux® 5.4, 5.5 et 5.6. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Guide de sécurité de Red Hat Enterprise Linux 5</i> </p> </td> 
  </tr> 
 </tbody> 
</table>

Voici quelques informations sur les méthodes permettant de réduire au minimum les vulnérabilités de sécurité du système d’exploitation :

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_whl_kjz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Elément </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Correctifs de sécurité </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Il existe un risque accru qu’un utilisateur non autorisé puisse accéder au serveur d’applications si les correctifs de sécurité et les mises à niveau du fournisseur ne sont pas appliqués en temps opportun. </p> <p>Remarque :  Assurez-vous de tester les correctifs de sécurité avant de les appliquer aux serveurs de production. </p> <p class="- topic/p ">Vous devez créer des stratégies et des procédures pour rechercher et installer régulièrement les correctifs. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Logiciel de protection antivirus </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Les analyseurs de virus peuvent identifier les fichiers infectés en recherchant une signature ou un comportement inhabituel. </p> <p>Les analyseurs conservent leurs signatures de virus dans un fichier, qui est généralement stocké sur le disque dur local. Les nouveaux virus sont souvent découverts, vous devez donc vous assurer que ce fichier est régulièrement mis à jour. Ainsi, les analyseurs de virus peuvent toujours identifier tous les virus actuels. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">NTP (Network Time Protocol) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Pour une bonne utilisation et une analyse médico-légale, veillez à ce que les serveurs et les conditionneurs DRM Primetime restent à l'heure exacte. Utilisez une version sécurisée de NTP pour synchroniser l'heure DRM Primetime sur tous les systèmes connectés à Internet. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Informations sur la sécurité du serveur d’applications {#section_22986936F1A547CEAB2D97E9E9D4825C}

Lorsque vous sécurisez votre serveur d’applications, vous devez mettre en oeuvre les mesures décrites par le revendeur de votre serveur.

Voici quelques-unes de ces mesures :

* Utilisation d’un nom d’utilisateur d’administrateur non évident
* Désactivation des services inutiles
* Sécurisation du gestionnaire de console
* Activation des cookies sécurisés
* Fermeture des ports inutiles
* Limitation des interfaces administratives par adresses ou domaines IP
* Utilisation de Java™ Security Manager

