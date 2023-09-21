---
title: Enregistrement de domaine de groupe de périphériques
description: Enregistrement de domaine de groupe de périphériques
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---

# Enregistrement de domaine de groupe de périphériques{#device-group-domain-registration}

Au lieu de lier une licence à un appareil spécifique, Primetime DRM 3.0 ou version ultérieure prend en charge la liaison de licences à un domaine d’appareil.

Plusieurs périphériques peuvent rejoindre un domaine et recevoir des jetons de domaine. Une fois qu’un appareil du domaine a acquis une licence, celle-ci peut être transférée à tout autre appareil du domaine, et ces appareils peuvent lire le contenu sans acquérir de licence directement à partir du serveur de licences.

Si vous souhaitez prendre en charge des licences liées à un domaine, la stratégie Primetime DRM doit spécifier le serveur de domaine avec lequel le client doit s’enregistrer. La stratégie DRM Primetime doit également spécifier les exigences d’authentification du serveur de domaine, que l’accès anonyme soit activé ou que le serveur nécessite une authentification personnalisée ou un nom d’utilisateur/mot de passe.

L’enregistrement de domaine et les licences liées aux domaines sont pris en charge par les clients DRM Primetime version 3.0 ou ultérieure. Si un client plus âgé ou un client Adobe Primetime 3.0 de Flash Player demande une licence pour du contenu prenant en charge l’enregistrement de domaine, le serveur de licences peut émettre une licence qui utilise une autre stratégie DRM Primetime pour prendre en charge la liaison à un appareil spécifique.
