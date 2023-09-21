---
title: Présentation du serveur de licences
description: Présentation du serveur de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Présentation {#license-server-overview}

Avant d’accorder des licences aux clients, vous devez déployer un serveur de licences Adobe Primetime DRM. Le serveur de licences utilise le SDK DRM Primetime pour effectuer un certain nombre de tâches.

Pour mettre en oeuvre un serveur de licences :

* Traitement des demandes d’authentification, si l’authentification par nom d’utilisateur/mot de passe est prise en charge.
* Traitement des demandes de licence
* Requêtes Process Get Server Version : tous les serveurs doivent mettre en oeuvre la prise en charge de ce type de requête.
* Traitement des demandes d’enregistrement de domaine : elles ne sont nécessaires que si vous implémentez un serveur de domaine.
* Traitement des demandes de désinscription de domaine : elles ne sont nécessaires que si vous implémentez un serveur de domaine.
* Synchronisation des processus : nécessaire uniquement si des licences spécifient les exigences de synchronisation.

En outre, le serveur doit fournir une logique métier pour authentifier les utilisateurs, déterminer si les utilisateurs sont autorisés à afficher le contenu et éventuellement suivre l’utilisation de la licence.

Voir *Référence de l’API DRM Adobe Primetime* pour plus d’informations sur l’API Java.
