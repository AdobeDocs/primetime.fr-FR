---
title: Présentation de la topologie réseau
description: Présentation de la topologie réseau
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---

# Présentation de la topologie réseau {#network-topology-overview}

Une fois que vous avez déployé Adobe Access, il est important de maintenir la sécurité de votre environnement. Cette section décrit les tâches nécessaires à la maintenance de la sécurité de votre serveur de production Adobe Access.

Utilisez une *proxy inverse* afin de s’assurer que différents ensembles d’URL pour les applications web d’accès aux Adobes sont disponibles pour les utilisateurs externes et internes. Cette configuration est plus sécurisée que la possibilité pour les utilisateurs de se connecter directement au serveur d’applications sur lequel Adobe Access est exécuté. Le proxy inverse exécute toutes les requêtes HTTP pour le serveur d’applications qui exécute Adobe Access. Les utilisateurs ne disposent que d’un accès réseau au proxy inverse et peuvent uniquement tenter les connexions URL prises en charge par le proxy inverse.

<!--<a id="fig-frx-dcg-44"></a>-->

![](assets/AdobeAccess_4_SecureDeployment_web.png)
