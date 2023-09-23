---
title: Déploiement de certificats
description: Déploiement de certificats
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# Déploiement de certificats{#deploy-certificates}

Pour éviter que le mot de passe PFX ne soit disponible en texte clair sur le serveur de licences, la mise en oeuvre de référence et le serveur Adobe Primetime DRM pour la diffusion protégée nécessitent que le mot de passe soit chiffré lorsqu’il est spécifié dans le fichier de configuration. Voir *Utilisation des implémentations de référence DRM Primetime* ou *Utilisation du serveur DRM Primetime* pour la diffusion en continu protégée pour obtenir des instructions sur l’exécution des utilitaires de brouillage. Chacun d’eux inclut son propre utilitaire de brouillon, et les mots de passe chiffrés ne sont pas interchangeables entre ces deux mises en oeuvre du serveur de licences.

Pour déployer les certificats et le mot de passe brouillé sur votre serveur de licences, voir *Utilisation des implémentations de référence DRM Primetime* ou *Utilisation du serveur DRM Primetime pour la diffusion en continu protégée*.
