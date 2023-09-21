---
title: Configuration d’un serveur de domaine
description: Configuration d’un serveur de domaine
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# Configuration d’un serveur de domaine{#set-up-a-domain-server}

Pour configurer un serveur de domaine sur une installation de serveur de licences existante :

1. Dans le [!DNL tomcat/lib] , ouvrez le répertoire [!DNL flashaccess-refimpl.properties] fichier .
1. Sous , `Domain CA certificate` , renseignez le certificat de l’autorité de certification du domaine.

   Ce certificat est ensuite utilisé pour accepter les jetons de domaine.
1. Sous , `Domain CA credential` , complétez la variable `Domain CA credential certificate (PFX)` détails.

   Ce certificat est ensuite utilisé pour signer des certificats de domaine et des jetons.
1. Spécifiez la valeur de `DomainServerlURL`.

   Si cette valeur est définie sur `NULL`, l’authentification de domaine peut réussir. Cependant, lors de la jointure au domaine, une erreur de jointure au domaine peut se produire.
