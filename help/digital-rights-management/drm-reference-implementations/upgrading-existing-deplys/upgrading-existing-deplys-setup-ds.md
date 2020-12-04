---
description: 'null'
seo-description: 'null'
seo-title: Configuration d’un serveur de domaine
title: Configuration d’un serveur de domaine
uuid: bf85305e-9a00-4bc0-ba36-c870979456e4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '95'
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
