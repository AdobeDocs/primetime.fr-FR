---
title: Configuration d’un serveur de domaine
description: Configuration d’un serveur de domaine
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# Configuration d’un serveur de domaine {#set-up-a-domain-server}

Pour configurer un serveur de domaine sur une installation de serveur de licences existante :

1. Dans le répertoire [!DNL tomcat/lib], ouvrez le fichier [!DNL flashaccess-refimpl.properties].
1. Sous l&#39;option `Domain CA certificate`, complétez le certificat d&#39;autorité de certification de domaine.

   Ce certificat est ensuite utilisé pour accepter les jetons de domaine.
1. Sous l&#39;option `Domain CA credential`, complétez les détails `Domain CA credential certificate (PFX)`.

   Ce certificat est ensuite utilisé pour la signature de certificats de domaine et de jetons.
1. Spécifiez la valeur de `DomainServerlURL`.

   Si cette valeur est définie sur `NULL`, l’authentification de domaine peut réussir. Cependant, lors de la jonction du domaine, une erreur de jonction de domaine peut se produire.
