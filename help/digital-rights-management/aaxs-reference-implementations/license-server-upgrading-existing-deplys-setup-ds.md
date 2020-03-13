---
seo-title: Configuration d’un serveur de domaine
title: Configuration d’un serveur de domaine
uuid: b262ea86-f465-4ed1-b278-122d4dafc881
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Configuration d’un serveur de domaine {#set-up-a-domain-server}

Pour configurer le serveur de domaine sur une installation existante du serveur de licences, effectuez le  suivant :

1. Ouvrez le [!DNL flashaccess-refimpl.properties] fichier sous [!DNL tomcat/lib].

1. Sous l’ `Domain CA certificate` option, renseignez les détails du certificat de l’autorité de certification de domaine. Ce certificat sera utilisé pour accepter les jetons de domaine.
1. Sous l’ `Domain CA credential` option, renseignez les `Domain CA credential certificate (PFX)` détails. Ce certificat sera utilisé pour la signature de certificats de domaine et de jetons.

1. Spécifiez la valeur pour `DomainServerlURL`. Si cette valeur est NULL, l’authentification de domaine peut réussir. Cependant, lors de la jonction du domaine, une erreur de jonction de domaine se produira.

