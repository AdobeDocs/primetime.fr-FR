---
title: Présentation de la topologie réseau
description: Présentation de la topologie réseau
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# Présentation {#network-topology-overview}

Une fois que vous avez déployé Adobe Primetime DRM, vous devez maintenir la sécurité du serveur de production Primetime DRM.

>[!NOTE]
>
>Primetime DRM était auparavant connu sous le nom d’accès aux Adobes, et avant cela, Flash Access.

Vous pouvez utiliser une *proxy inverse* pour s’assurer que différents ensembles d’URL pour les applications web Primetime DRM sont disponibles pour les utilisateurs externes et internes. *Reverse proxy* est plus sécurisé que de permettre aux utilisateurs de se connecter directement au serveur d’applications sur lequel Primetime DRM s’exécute. Cette configuration exécute toutes les requêtes HTTP pour le serveur d’applications qui exécute Primetime DRM. Les utilisateurs peuvent accéder uniquement au proxy inverse et uniquement aux connexions URL prises en charge par le proxy inverse.

<!--<a id="fig_8083A8C794B646CD87985EC891B60663"></a>-->

![](assets/AdobeAccess_4_SecureDeployment.png)
