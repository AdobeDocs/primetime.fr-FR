---
title: Présentation de la topologie du réseau
description: Présentation de la topologie du réseau
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Présentation de la topologie du réseau {#network-topology-overview}

Une fois que vous avez déployé Adobe Access avec succès, il est important de maintenir la sécurité de votre environnement. Cette section décrit les tâches nécessaires pour maintenir la sécurité de votre serveur de production Adobe Access.

Utilisez un *proxy inverse* pour vous assurer que différents ensembles d&#39;URL pour les applications Web d&#39;accès à l&#39;Adobe sont disponibles pour les utilisateurs externes et internes. Cette configuration est plus sécurisée que si vous autorisiez les utilisateurs à se connecter directement au serveur d’applications sur lequel Adobe Access s’exécute. Le proxy inverse exécute toutes les requêtes HTTP pour le serveur d’applications qui exécute Adobe Access. Les utilisateurs disposent uniquement d’un accès réseau au proxy inverse et peuvent uniquement tenter les connexions URL prises en charge par le proxy inverse.

<!--<a id="fig-frx-dcg-44"></a>-->

![](assets/AdobeAccess_4_SecureDeployment_web.png)

