---
title: Éléments NON pris en charge par Primetime Cloud DRM
description: Éléments NON pris en charge par Primetime Cloud DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---

# Éléments NON pris en charge par Primetime Cloud DRM{#what-is-not-supported-by-primetime-cloud-drm}

Primetime Cloud DRM prend en charge presque toutes les fonctionnalités actuellement disponibles avec Primetime DRM. Cependant, en raison de certaines fonctionnalités DRM nécessitant une communication avec le sous-système de règles métier principal d’un client, certaines fonctionnalités ne sont pas disponibles avec Primetime Cloud DRM.

Les fonctionnalités actuellement non prises en charge par Primetime Cloud DRM sont les suivantes :

* Contenu fourni avec un CEK externe (où le serveur de licences demande le CEK du contenu à partir d’un système de gestion des clés externe)
* Domaines d’appareil
* Chaîne de licence avancée
* Retour/révocation de licence
* PHLS/PHDS. Il s’agit de programmes de protection qui n’utilisent pas de serveur de licences.
* Authentification de l’utilisateur/mot de passe
