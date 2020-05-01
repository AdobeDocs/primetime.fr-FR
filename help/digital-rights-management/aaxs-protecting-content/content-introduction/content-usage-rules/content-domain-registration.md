---
seo-title: Enregistrement du domaine du groupe de périphériques
title: Enregistrement du domaine du groupe de périphériques
uuid: fd559175-2c3c-4d71-bfa1-8de9907d2b7c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Enregistrement du domaine du groupe de périphériques{#device-group-domain-registration}

Au lieu de lier une licence à un périphérique spécifique, Adobe Access 3.0 et les versions ultérieures prennent en charge la liaison de licences à un domaine de périphérique. Plusieurs périphériques peuvent rejoindre un domaine et recevoir des jetons de domaine. Une fois qu’un périphérique du domaine a acquis une licence, celle-ci peut être transférée à tout autre périphérique du domaine, et ces périphériques peuvent lire le contenu sans acquérir de licence directement auprès du serveur de licences.

Pour prendre en charge les licences liées aux domaines, la stratégie doit spécifier le serveur de domaine avec lequel le client doit s’enregistrer. La stratégie spécifie également les exigences d’authentification pour le serveur de domaine (que l’accès anonyme soit autorisé ou que le serveur nécessite un nom d’utilisateur/mot de passe ou une authentification personnalisée).

L’enregistrement des domaines et les licences liées aux domaines sont pris en charge par les clients Adobe Access versions 3.0 et ultérieures. Si un client plus âgé ou un client Adobe Access 3.0 de Flash Player demande une licence pour le contenu qui prend en charge l’enregistrement de domaine, le serveur de licences peut émettre une licence en utilisant une autre stratégie qui prend en charge la liaison à un périphérique spécifique.
