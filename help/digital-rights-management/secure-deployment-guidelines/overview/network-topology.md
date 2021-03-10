---
title: Présentation de la topologie du réseau
description: Présentation de la topologie du réseau
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# Aperçu {#network-topology-overview}

Une fois que vous avez déployé Adobe Primetime DRM, vous devez conserver la sécurité du serveur de production DRM Primetime.

>[!NOTE]
>
>Primetime DRM était auparavant connu sous le nom d&#39;Adobe Access, et avant cela, Flash Access.

Vous pouvez utiliser un *proxy inverse* pour vous assurer que différents ensembles d’URL pour les applications Web DRM Primetime sont disponibles pour les utilisateurs externes et internes. *Le* proxyde inverse est plus sécurisé que de permettre aux utilisateurs de se connecter directement au serveur d’applications sur lequel Primetime DRM s’exécute. Cette configuration exécute toutes les requêtes HTTP pour le serveur d’applications qui exécute Primetime DRM. Les utilisateurs peuvent accéder uniquement au proxy inverse et uniquement aux connexions URL prises en charge par le proxy inverse.

<!--<a id="fig_8083A8C794B646CD87985EC891B60663"></a>-->

![](assets/AdobeAccess_4_SecureDeployment.png)