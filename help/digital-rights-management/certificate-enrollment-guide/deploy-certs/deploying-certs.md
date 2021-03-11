---
title: Déploiement de certificats
description: Déploiement de certificats
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# Déploiement de certificats{#deploy-certificates}

Pour éviter que le mot de passe PFX ne soit disponible en texte clair sur le serveur License Server, la mise en oeuvre de référence et le serveur Adobe Primetime DRM Server pour la diffusion en flux continu protégée exigent que le mot de passe soit chiffré lorsqu&#39;il est spécifié dans le fichier de configuration. Voir *Utilisation des implémentations de référence DRM de Primetime* ou *Utilisation du serveur DRM de Primetime* pour la diffusion en flux continu protégée pour obtenir des instructions sur l&#39;exécution des utilitaires de brouillage. Chacun d&#39;eux inclut son propre utilitaire de brouillon, et les mots de passe chiffrés ne sont pas interchangeables entre ces deux implémentations du serveur de licences.

Pour déployer les certificats et le mot de passe brouillé sur votre serveur de licences, voir *Utilisation des implémentations de référence DRM de Primetime* ou *Utilisation du serveur DRM de Primetime pour la diffusion en continu protégée*.
