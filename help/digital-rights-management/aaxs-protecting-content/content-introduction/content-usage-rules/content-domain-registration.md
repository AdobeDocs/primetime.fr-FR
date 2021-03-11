---
title: Enregistrement du domaine du groupe de périphériques
description: Enregistrement du domaine du groupe de périphériques
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Enregistrement du domaine du groupe de périphériques{#device-group-domain-registration}

Au lieu de lier une licence à un périphérique spécifique, Adobe Access 3.0 et les versions ultérieures prennent en charge la liaison de licences à un domaine de périphérique. Plusieurs périphériques peuvent rejoindre un domaine et recevoir des jetons de domaine. Une fois qu’un périphérique du domaine a acquis une licence, celle-ci peut être transférée à tout autre périphérique du domaine, et ces périphériques peuvent lire le contenu sans acquérir de licence directement auprès du serveur de licences.

Pour prendre en charge les licences liées aux domaines, la stratégie doit spécifier le serveur de domaine avec lequel le client doit s’enregistrer. La stratégie spécifie également les exigences d’authentification pour le serveur de domaine (que l’accès anonyme soit autorisé ou que le serveur nécessite un nom d’utilisateur/mot de passe ou une authentification personnalisée).

L&#39;enregistrement des domaines et les licences liées aux domaines sont pris en charge par les clients Adobe Access version 3.0 et ultérieure. Si un client plus âgé ou un client Adobe Access 3.0 dans un Flash Player demande une licence pour le contenu qui prend en charge l&#39;enregistrement de domaine, le serveur de licences peut émettre une licence en utilisant une autre stratégie qui prend en charge la liaison à un périphérique spécifique.
