---
seo-title: Enregistrement de domaine de groupe de périphériques
title: Enregistrement de domaine de groupe de périphériques
uuid: 221bf6c3-0568-443d-b761-64715a57ada6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Enregistrement de domaine de groupe de périphériques{#device-group-domain-registration}

Plutôt que de lier une licence à un périphérique spécifique, Primetime DRM 3.0 ou version ultérieure prend en charge la liaison de licences à un domaine de périphérique.

Plusieurs périphériques peuvent rejoindre un domaine et recevoir des jetons de domaine. Une fois qu’un périphérique du domaine a acquis une licence, celle-ci peut être transférée à tout autre périphérique du domaine, et ces périphériques peuvent lire le contenu sans acquérir de licence directement auprès du serveur de licences.

Si vous souhaitez prendre en charge des licences liées à un domaine, la stratégie DRM Primetime doit spécifier le serveur de domaine avec lequel le client doit s’enregistrer. La stratégie DRM Primetime doit également spécifier les exigences d’authentification pour le serveur de domaine, que l’accès anonyme soit activé ou que le serveur nécessite un nom d’utilisateur/mot de passe ou une authentification personnalisée.

L’enregistrement de domaine et les licences liées aux domaines sont pris en charge par les clients DRM Primetime version 3.0 ou ultérieure. Si un client plus âgé ou un client Adobe Primetime 3.0 dans Flash Player demande une licence pour le contenu prenant en charge l’enregistrement de domaine, le serveur de licences peut émettre une licence qui utilise une autre stratégie DRM Primetime pour prendre en charge la liaison à un périphérique spécifique.
