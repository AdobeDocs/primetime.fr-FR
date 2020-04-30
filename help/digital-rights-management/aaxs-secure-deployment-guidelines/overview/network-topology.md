---
seo-title: Présentation de la topologie du réseau
title: Présentation de la topologie du réseau
uuid: 1558b7fa-dc0d-477c-8f1c-9c6f3718e1b0
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Présentation de la topologie du réseau {#network-topology-overview}

Une fois Adobe Access déployé avec succès, il est important de maintenir la sécurité de votre environnement. Cette section décrit les tâches nécessaires pour maintenir la sécurité de votre serveur de production Adobe Access.

Utilisez un proxy ** inverse pour vous assurer que différents ensembles d’URL pour les applications Web Adobe Access sont disponibles pour les utilisateurs externes et internes. Cette configuration est plus sécurisée que si vous autorisiez les utilisateurs à se connecter directement au serveur d’applications sur lequel Adobe Access s’exécute. Le proxy inverse exécute toutes les requêtes HTTP pour le serveur d’applications qui exécute Adobe Access. Les utilisateurs disposent uniquement d’un accès réseau au proxy inverse et peuvent uniquement tenter les connexions URL prises en charge par le proxy inverse.

<!--<a id="fig-frx-dcg-44"></a>-->

![](assets/AdobeAccess_4_SecureDeployment_web.png)

