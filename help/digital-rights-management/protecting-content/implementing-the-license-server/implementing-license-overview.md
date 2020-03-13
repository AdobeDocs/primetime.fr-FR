---
seo-title: Présentation du serveur de licences
title: Présentation du serveur de licences
uuid: 8c62376b-b159-4297-9322-75d62947e84e
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Présentation {#license-server-overview}

Avant de pouvoir attribuer des licences à des clients, vous devez déployer un serveur de licences DRM Adobe Primetime. Le serveur de licences utilise le SDK DRM Primetime pour effectuer un certain nombre de .

Pour mettre en oeuvre un serveur de licences :

* Traitez les demandes d’authentification, si l’authentification par nom d’utilisateur/mot de passe est prise en charge.
* Traiter les demandes de licence
* Demandes d’obtention de version de serveur de processus : tous les serveurs doivent mettre en oeuvre la prise en charge de ce type de demande.
* Traiter les demandes d&#39;enregistrement de domaine : uniquement nécessaire si vous implémentez un serveur de domaine.
* Traiter les demandes de désenregistrement de domaine : uniquement nécessaire si vous implémentez un serveur de domaine.
* Synchronisation des processus: uniquement nécessaire si les licences spécifient les exigences de synchronisation.

En outre, le serveur doit fournir une logique métier pour authentifier les utilisateurs, déterminer si les utilisateurs sont autorisés à du contenu et, éventuellement, suivre l’utilisation des licences.

Pour plus d’informations sur l’API Java, consultez le Guide de référence *de l’API DRM* Adobe Primetime.
