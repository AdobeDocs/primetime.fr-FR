---
title: Présentation du serveur de licences
description: Présentation du serveur de licences
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Aperçu {#license-server-overview}

Avant de pouvoir délivrer des licences à des clients, vous devez déployer un serveur de licences Adobe Primetime DRM. Le serveur de licences utilise le SDK DRM Primetime pour effectuer un certain nombre de tâches.

Pour mettre en oeuvre un serveur de licences :

* Traitez les demandes d’authentification si l’authentification par nom d’utilisateur/mot de passe est prise en charge.
* Traiter les demandes de licence
* Traiter les demandes d&#39;obtention de version de serveur : tous les serveurs doivent mettre en oeuvre la prise en charge de ce type de demande.
* Traiter les demandes d&#39;enregistrement de domaine : uniquement nécessaire si vous implémentez un serveur de domaine.
* Traiter les demandes de désenregistrement de domaine : uniquement nécessaire si vous implémentez un serveur de domaine.
* Synchronisation des processus : uniquement nécessaire si des licences spécifient les exigences de synchronisation.

En outre, le serveur doit fournir une logique métier pour authentifier les utilisateurs, déterminer si les utilisateurs sont autorisés à vue du contenu et éventuellement suivre l’utilisation des licences.

Voir *Référence de l’API DRM d’Adobe Primetime* pour plus d’informations sur l’API Java.
