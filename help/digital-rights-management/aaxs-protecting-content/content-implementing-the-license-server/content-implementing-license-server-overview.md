---
seo-title: Présentation
title: Présentation
uuid: f4ae10ca-6e2a-4313-80a0-4c7377dba000
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Présentation{#overview}

Pour délivrer des licences aux clients, vous devez déployer un serveur de licences Adobe Access. Le serveur de licences utilise le SDK Adobe® Access™ pour effectuer les  suivantes :

* Traitez les demandes d’authentification, si l’authentification par nom d’utilisateur/mot de passe est prise en charge.
* Traiter les demandes de licence
* Demandes d&#39;obtention de version de serveur de processus : tous les serveurs doivent implémenter la prise en charge de ce type de requête.
* Traiter les demandes d&#39;enregistrement de domaine : uniquement nécessaire si vous implémentez un serveur de domaine.
* Traiter les demandes de désenregistrement de domaine : uniquement nécessaire si vous implémentez un serveur de domaine.
* Synchronisation des processus — Uniquement nécessaire si les licences spécifient les exigences de synchronisation.

En outre, le serveur doit fournir une logique métier pour authentifier les utilisateurs, déterminer si les utilisateurs sont autorisés à du contenu et, éventuellement, suivre l’utilisation des licences.

Pour plus d’informations sur l’API Java abordée dans ce chapitre, voir Référence *sur l’API d’accès* Adobe.
