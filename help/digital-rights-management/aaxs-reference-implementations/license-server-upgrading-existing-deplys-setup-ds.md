---
title: Configuration d’un serveur de domaine
description: Configuration d’un serveur de domaine
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Configuration d’un serveur de domaine {#set-up-a-domain-server}

Pour configurer le serveur de domaine sur une installation de serveur de licences existante, effectuez les tâches suivantes :

1. Ouvrez le [!DNL flashaccess-refimpl.properties] fichier sous [!DNL tomcat/lib].

1. Sous , `Domain CA certificate` , renseignez les détails du certificat de l’autorité de certification du domaine. Ce certificat sera utilisé pour accepter les jetons de domaine.
1. Sous , `Domain CA credential` , renseignez la variable `Domain CA credential certificate (PFX)` détails. Ce certificat sera utilisé pour la signature des certificats de domaine et des jetons.

1. Spécifiez la valeur de `DomainServerlURL`. Si cette valeur est NULL, l’authentification de domaine peut réussir. Cependant, lors de l’accès au domaine, une erreur de jointure de domaine se produira.
