---
description: 'null'
seo-description: 'null'
seo-title: Configuration d’un serveur de domaine
title: Configuration d’un serveur de domaine
uuid: bf85305e-9a00-4bc0-ba36-c870979456e4
translation-type: tm+mt
source-git-commit: ''

---


# Configuration d’un serveur de domaine{#set-up-a-domain-server}

Pour configurer un serveur de domaine sur une installation de serveur de licences existante :

1. Dans le [!DNL tomcat/lib] répertoire, ouvrez le [!DNL flashaccess-refimpl.properties] fichier.
1. Sous l’ `Domain CA certificate` option, complétez le certificat d’autorité de certification de domaine.

   Ce certificat est ensuite utilisé pour accepter les jetons de domaine.
1. Sous l’ `Domain CA credential` option, complétez les `Domain CA credential certificate (PFX)` détails.

   Ce certificat est ensuite utilisé pour la signature de certificats de domaine et de jetons.
1. Spécifiez la valeur de `DomainServerlURL`.

   Si cette valeur est définie sur `NULL`, l’authentification de domaine peut réussir. Cependant, lors de la jonction du domaine, une erreur de jonction de domaine peut se produire.
