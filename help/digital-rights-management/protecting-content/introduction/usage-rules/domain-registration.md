---
title: Enregistrement du domaine du groupe de périphériques
description: Enregistrement du domaine du groupe de périphériques
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---


# Enregistrement du domaine du groupe de périphériques{#device-group-domain-registration}

Comme alternative à la liaison d’une licence à un périphérique spécifique, Primetime DRM 3.0 ou version ultérieure prend en charge la liaison de licences à un domaine de périphérique.

Plusieurs périphériques peuvent rejoindre un domaine et recevoir des jetons de domaine. Une fois qu’un périphérique du domaine a acquis une licence, celle-ci peut être transférée à tout autre périphérique du domaine, et ces périphériques peuvent lire le contenu sans acquérir de licence directement auprès du serveur de licences.

Si vous souhaitez prendre en charge des licences liées à un domaine, la stratégie DRM de Primetime doit spécifier le serveur de domaine avec lequel le client doit s’enregistrer. La stratégie DRM de Primetime doit également spécifier les exigences d&#39;authentification du serveur de domaine, que l&#39;accès anonyme soit activé ou que le serveur nécessite un nom d&#39;utilisateur/mot de passe ou une authentification personnalisée.

L’enregistrement de domaine et les licences liées aux domaines sont pris en charge par les clients DRM Primetime version 3.0 ou ultérieure. Si un client plus âgé ou un client Adobe Primetime 3.0 en Flash Player demande une licence pour le contenu qui prend en charge l’enregistrement de domaine, le serveur de licences peut émettre une licence qui utilise une autre stratégie DRM Primetime pour prendre en charge la liaison à un périphérique spécifique.
